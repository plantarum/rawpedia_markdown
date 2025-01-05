The "Performance" tab is only for people who know what they're doing. It
lets you poke under the hood and tweak the parameters of some tools.
These parameters take part in the balance between speed and stability.

## Maximum Number of Threads for Noise Reduction

The [Noise Reduction](Noise_Reduction "wikilink") algorithm in
RawTherapee is very powerful. It is also quite CPU and memory intensive.
People with weak hardware who experience crashes caused by running out
of RAM may find that tweaking this parameter prevents those crashes, at
the cost of longer processing time.

[Noise Reduction](Noise_Reduction "wikilink") has a baseline requirement
of 128MB of RAM for a 10 megapixel raw photo, or 512MB of RAM for a 40
megapixel one, and additionally 128MB of RAM per thread. The more
threads run in parallel, the quicker the computation, but higher the
memory requirement.

Most modern CPUs run two threads per physical core. Find out what CPU
you have and how many cores it has, multiply that by two, and you get
the maximum number of threads it would make sense to run simultaneously.
Let's call this number *T<sub>max</sub>*. You would not benefit from
running more threads than this - in fact you would likely suffer a small
speed penalty.

Setting this parameter to "0" will let your CPU figure out what
*T<sub>max</sub>* is, and use that. If you experience crashes due to
insufficient RAM, then you can calculate *T<sub>max</sub>* yourself and
use a number lower than that.