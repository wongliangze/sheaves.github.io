---
layout: post
title: Animated GIFs
tag: 
- Uncategorized
---

I really should be posting about character theory, but I got distracted making some aesthetic changes to this blog (new icon and favicon!) and creating animations like this:

![harmonograph](/images/harmonograph_loop.gif)

<!--more-->

<div class="no_out">
  <script type="text/x-sage">
d,c,p,k = [0.01, 0.05, -0.15, 0.05]
x(t,u) = (sin(t*2*pi) + sin((1-c + u*c*2)*t*2*pi) + p*pi)*exp(-d*t)
y(t,u) = (sin((1-c+ 0.55*c*2)*t*2*pi + k*(1-u)*pi) + cos((1-c + 0.9*c*2)*t*2*pi) + p*pi)*exp(-d*t)
  
a = animate([parametric_plot((x(t,u),y(t,u)),(t,0,30),color = [u,1-u,0.52], axes= False, plot_points = 200) for u in [0.48+0.45*sin(v) for v in srange(0,2*pi,0.1)]])
a.gif(savefile='my_animation.gif', delay=20, iterations=0)
  </script>
</div>


  
I'm not putting this in a SageCell because this could take quite a while, especially if you increase the number of frames (by changing the parameters in `srange`), but feel free to try it out on your own copy of Sage. It saves an animated GIF that loops forever (`iterations = 0`) at the location specified by `savefile`.

For more information, checkout the [Sage reference for animated plots](http://www.sagemath.org/doc/reference/plotting/sage/plot/animate.html).
