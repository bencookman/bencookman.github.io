---
# the default layout is 'page'
icon: fa-solid fa-camera-retro
order: 5
---


{% assign gallery_style = 'padding:10px;filter:drop-shadow(0em 0em 0.25em black);' %}
{% assign gallery_style_left = 'float:left;padding:10px;filter:drop-shadow(0em 0em 0.5em black);' %}

# Contents

<!-- [Link text]({{ 'relative-url' | relative_url }}) -->
<!-- [Link text](#heading-name-snail-case) -->

- [Mandelbrot Set in the Command Line](#mandelbrot-set-in-the-command-line)
- [Combustion and Flames](#combustion-and-flames)
- [Stability Regions of Time Integrators](#stability-regions-of-time-integrators)



# Mandelbrot Set in the Command Line

This project (which I will write more about later) was a C# implementation of the [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set) I made when I was 18. Below are a collection of screenshots taken from the program, dubbed 'Consolebrot'. I have a newer version of this application written in [Zig](https://ziglang.org/) that I am currently developing at [this GitHub repository](https://github.com/bencookman/consolebrot-zig).

<div>
  {% assign size_consolebrot = '375px' %}
  <img src="assets/ben-assets/gallery-imgs/consolebrot-1.png" alt="Mandelbrot in a console zoomed out" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-2.png" alt="Mandelbrot in a console zoomed in" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-3.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-4.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-5.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-6.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-7.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-8.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-9.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-10.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-11.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-12.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-13.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-14.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
  <img src="assets/ben-assets/gallery-imgs/consolebrot-15.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style_left }}">
  <img src="assets/ben-assets/gallery-imgs/consolebrot-16.png" alt="" style="width:{{ size_consolebrot }};{{ gallery_style }}">
  <br>
</div>
<br>


# Combustion and Flames
As mentioned [here]({{ '/about/#current-position' | relative_url }}), my PhD studies focus on combustion and the dynamics, stability and shape of flame fronts. In time I'll add photos to this section!

COMING SOON (/◕ヮ◕)/


# Stability Regions of Time Integrators
My master's thesis was about parallel in time integrators. The most visually pleasing part of this research are the stability regions, which if coloured well can produce some really nice patterns. The Runge-Kutta methods, for example, produce [this pattern](https://www.chebfun.org/examples/ode-linear/img/Regions_02.png) for orders 1 to 4.

COMING SOON (/◕ヮ◕)/
