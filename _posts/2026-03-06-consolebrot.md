---
title: The Mandelbrot Set, Visualised in a Terminal
date: 2026-03-08 00:00:00 +0000
categories: [Maths]
# tags: [maths, signal processing, fft, window functions]     # TAG names should always be lowercase
tags: [maths, mandelbrot, complex analysis, fractals, iteration]     # TAG names should always be lowercase
math: true
---

Fractals are shapes, usually produced by some iterative process, which possess infinitely detailed structures at their boundary. It turns out these fractals pop up in loads of different places in Mathematics, which is lovely as it gives us plenty of practice coding different programming languages. At least, that's what I decided to do, using the Mandelbrot set as inspiration for a program ran in the console which displays the fractal.

*(This is a short post, because the my initial idea and the primary algorithm written below are both pretty straightforward. I'm really not sure I could do any better a job explaining/motivating these topics --- especially the Mandelbrot set --- than those who've talked about this stuff on the internet before.)*

## The Mandelbrot Set

One fractal, [the Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set), is produced by choosing a complex number $c$ and iterating with the formula $z_{n+1} = z_{n}^2 + c$ where $z_0 = 0$. If the sequence $z_n$ diverges, then the value $c$ is not in the Mandelbrot set, otherwise the value is in the Mandelbrot set (this includes cycles which do not diverge). Below is an image showing the set in black on an complex plane with those points not in the plane coloured depending on how fast they diverge, darker means divergence is faster.

![]({{ site.base_url }}/assets/img/consolebrot/Mandel_zoom_00_mandelbrot_set.jpg){: width="560" }
*Courtesy of Wikipedia. Everyone say: "Thank you, Wikipedia!"*

A beautiful property of these fractals is how the structure of their boundaries have infinite detail, no matter how far you might zoom in. This property is explored in much more detail for a different fractal --- produced by Newton iteration --- by 3blue1brown in the video below (isn't this just one of the prettiest YouTube thumbnails you've ever seen):

<div style="display:flex;justify-content:center;align-items:center;padding-bottom:20px;">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/-RdOwhmqP5s?si=CLembfSdDrAXbhI-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" style="" allowfullscreen></iframe>
</div>

This makes them an excellent target for mobile and web apps such as [this one](https://www.zazow.com/mandelbrot/create.php). The idea I had, then, was to remove almost all of the sharpness in the images you will usually see by rendering the Mandelbrot set as characters in a terminal? This should result in an program running in a resizeable terminal to produce ASCII art of any dimension which can be easily copied!

## Zig 

This is all, of course, just an excuse to learn a fancy new programming language I'd heard about on the internet and gotten far too excited about. In this case, I've actually already tried this project out before as an idea I had when I was 18 and solved using C# [at this GitHub repository](https://github.com/bencookman/consolebrot-cs). Needless to say, I was a lot worse at coding back then --- all I had use programming for up to that point was to make a shoddy game in Unity and code IT homework --- which lead to a mess of a program I've got no interest in improving or maintaining. It worked though, albeit with some hefty restrictions: it only works on Windows, the console window cannot be resized and the program has to be run by clicking on the `.exe` file to open it, not by running it from an existing terminal. I'd like to say having coded a version of this before that I'd have something of a leg-up, but it's such a simple algorithm to code I'm not sure it makes a difference.

This time, instead of C# I'm using a much newer language called [**Zig**](https://ziglang.org/), which claims to be a replacement for C as a low-level system's language with nicer syntax, numeric types, error handling and more. For this purpose, using Zig doesn't necessarily make the most sense as high-level languages can probably do the same thing with less strife. That said, any low-level language should be able to do anything those higher-level languages can. Besides, this is a great excuse not to use C, right?

## The Program

Ignoring all the build system and low-level riff-raff, the program can be boiled down to some simple pseudocode:

```pseudocode
Repeat on key press {
    Register what key was pressed and act on it (e.g. Up Arrow translates
        complex plane visible upwards, Page Up zooms in on the centre point
        of the visible complex plane);
    Recognise size of console and map each character in the window to a
        coordinate in the complex plane;
    For each character's coordinate, set this as c and iterate, as above {
        Set the character depending on if:
        (1) c does not diverge after N iterations (c is in the Mandelbrot set);
        (2) c diverges only after N-M  iterations (c is outside of the
            Mandelbrot set, but zooming in may introduce more detail
            for those points (1) nearby);
        (3) c diverges at or before N-M iterations (c is outside of the
            Mandelbrot set);
        (E.g. (1) => 'O', (2) => '.', (3) => ' ' and N = 100, M = 5)
    }
}
```

It turns out the only real difficulty, given that Zig has native access to complex numbers, is making sure the correct ASCII escape sequences are used to keep the console screen looking nice to avoid the issues I'd had with the aforementioned C# program. Even still, I hadn't bothered using arbitrary precision complex numbers (since this seems like a massive hassle in every language I've ever used), so there's a maximum amount you can zoom in before the 'image' becomes blocky due to a lack of precision. There might be some way of factorising out the 'zooming factor' from the iteration as a means of circumventing this problem, but I struggle to figure out how. 

The source code can be seen and downloaded [at this GitHub repository](https://github.com/bencookman/consolebrot-zig) --- follow the directions given on the README for installation instructions (it's pretty simple). Note that you'll need Zig version at least `0.15.2` for it to work, which can be downloaded and installed [following these instructions](https://zig.guide/getting-started/installation/).

## Results

Here is some the ASCII, copied directly from terminal output.

**The first characters you meet in the console:**

```ascii
                                            0                         
                                         0000000                      
                                           0000                       
                                  00 00000000000000                   
                                  0000000000000000000000              
                               00000000000000000000000000             
                              00000000000000000000000000000           
                  0 00        0000000000000000000000000000            
                 0000000000  00000000000000000000000000000            
                000000000000 0000000000000000000000000000             
000000000000000000000000000000000000000000000000000000                
                000000000000 0000000000000000000000000000             
                 0000000000  00000000000000000000000000000            
                  0 00        0000000000000000000000000000            
                              00000000000000000000000000000           
                               00000000000000000000000000             
                                  0000000000000000000000              
                                  00 00000000000000                   
                                           0000                       
                                         0000000                      
                                            0                         
```

**Then zooming in on one of the top left lobes:**

```ascii
                                                                      
                    0                                                 
                 0        0                                         0 
                                                                      
                      00000  0   0                                    
                  0   0000000  0 00   000                  0          
                      000000000000000000  0  0              00     0  
                         00000000000000000 0                0000000 00
                      0000000000000000000000            0  00000000000
                     0000000000000000000000000       0 0 0000000000000
                   0  000000000000000000000000 0   000 000000000000000
                 0 000000000000000000000000000   00 000000000000000000
                    0 00000000000000000000000  00000000000000000000000
                      0000000000000000000000 0000000000000000000000000
                       00000000000000000000000000000000000000000000000
                          00000000000000000000000000000000000000000000
                           00 00 00  000000000000000000000000000000000
                                00000000000000000000000000000000000000
                             0 000000000000000000000000000000000000000
                    0 0   00000000000000000000000000000000000000000000
               0    00000000000000000000000000000000000000000000000000
```

**Even further:**

```ascii
       00  00 0  0000000    0  00                                     
      0    00   00000000         0                                    
      0 0        000000 000                                           
    0         0    0 00                                               
0  0          0     00   0  0                                         
   00              0 0                          0                     
                    00   0                       0         0 0     0  
            0      00 0  0                     0 0                    
            0 00 0 0000         0                    0                
              0  0 000    00                        0        0        
   0             0  00            0       0          0       0        
                  0  00        0 0    0    0  00        0             
 0    0 0     0    0 00  0 00000    00     00     0                   
  00    0   0 0  0  0000      0      0 0     00                       
 0 000000     0000000 0   0         0 00      0            0          
   0 00000 00000000000                           0         0          
     000000000000000  0               0                               
0 000000000000000000         0                                        
  00000000000000000  0  0      0                                      
0000000000000000000000000000                 0                        
000000000000000000000000       00           0     0                   
```

**And eventually, even the recognisable Mandelbrot 'bulbs' become scarce:**

```ascii
        00  000                00 0000          0000                  
       00000000                 00 0000    0      00 00               
0      000000000 00               0000      00000000                  
0000     00000  00           00000000    000000 00                    
000000000000000              000 0000   0000                          
0000000000000    0               00000 000000000000 0                 
0000000000000  00000            000000000000000 00000 0               
00000000000000000000               00000000000000                     
000000000000000000000000            0 000000000000                    
000000000000000000000                  000000   00000 0               
0000000000000000000000    0 00 00   000000000    00000   00    0      
00000000000000000000000  00000000000000000 0     000000  0000         
000    000000000000000000000000000000000000       00000000000         
 0      000000000000000000000000000000000000        000    0          
        000000000000000000000000000000   0                   00       
          00000000000000000000000                                     
     0   000000000000000000000000                                     
    00000000000000000000000000000   00000 00                          
   0000000000000000000    0000000000000 00                            
    0000    0000000000    000000000000000                             
     0         000   00        00000000 00000                         
```



