# ProgressTimer

This package implements a light-weight and easy to use timing functionality for Julia when you know the number of iterations that need to take place.

If you want more advanced features please see the package [ProgressMeter](https://github.com/timholy/ProgressMeter.jl).

Activate the package as usual using

```julia
using ProgressTimter
```

To start the timer call `TimingInit()` and store the output into a variable

```julia
TS=TimingInit()
```

To trigger printing simply by calling `TimingProgress(TS,Nr,NSamples)` and store the output again.

```julia
for n in 1:NSamples
    ###
    ### Some computation
    ###
    TS=TimingProgress(TS,n,NSamples)
end
```

The ProgressTimer will at most print onve every secnt and will dynamically change to print every minute and every hour as the loop proceeds.
An actuall use case could look as this.

```
###Prints every second
47 done 999953 to go. Time: 1 sec. Time left: 6.0 hr of 6.0 hr.
94 done 999906 to go. Time: 2 sec. Time left: 6.0 hr of 6.0 hr.
151 done 999849 to go. Time: 3 sec. Time left: 5.6 hr of 5.6 hr.
209 done 999791 to go. Time: 4 sec. Time left: 5.4 hr of 5.4 hr.
559 done 999441 to go. Time: 10 sec. Time left: 5.0 hr of 5.0 hr.
...
3218 done 996782 to go. Time: 58 sec. Time left: 4.9 hr of 5.0 hr.
3273 done 996727 to go. Time: 59 sec. Time left: 5.0 hr of 5.0 hr.
3331 done 996669 to go. Time: 60 sec. Time left: 4.9 hr of 5.0 hr.
###Changing to printing every minute
3384 done 996616 to go. Time: 1.0 min. Time left: 5.0 hr of 5.0 hr.
6738 done 993262 to go. Time: 2.0 min. Time left: 4.9 hr of 5.0 hr.
10096 done 989904 to go. Time: 3.0 min. Time left: 4.9 hr of 5.0 hr.
...
199757 done 800243 to go. Time: 57.0 min. Time left: 3.8 hr of 4.8 hr.
203385 done 796615 to go. Time: 58.0 min. Time left: 3.8 hr of 4.8 hr.
207110 done 792890 to go. Time: 59.0 min. Time left: 3.8 hr of 4.7 hr.
###Changing to printing every hour
210831 done 789169 to go. Time: 1.0 hr. Time left: 3.7 hr of 4.7 hr.
440424 done 559576 to go. Time: 2.0 hr. Time left: 2.5 hr of 4.5 hr.
654557 done 345443 to go. Time: 3.0 hr. Time left: 1.6 hr of 4.6 hr.
###Almost an hour left, prints once per minute
786170 done 213830 to go. Time: 3.7 hr. Time left: 1.0 hr of 4.7 hr.
786226 done 213774 to go. Time: 3.7 hr. Time left: 60.0 min of 4.7 hr.
789497 done 210503 to go. Time: 3.7 hr. Time left: 59.1 min of 4.7 hr.
792736 done 207264 to go. Time: 3.7 hr. Time left: 58.2 min of 4.7 hr.
....
982114 done 17886 to go. Time: 4.6 hr. Time left: 5.0 min of 4.7 hr.
985917 done 14083 to go. Time: 4.6 hr. Time left: 4.0 min of 4.7 hr.
989690 done 10310 to go. Time: 4.6 hr. Time left: 2.9 min of 4.7 hr.
993406 done 6594 to go. Time: 4.6 hr. Time left: 1.8 min of 4.7 hr.
###Almost a minute left, prints once per second
996603 done 3397 to go. Time: 4.7 hr. Time left: 57 sec of 4.7 hr.
996672 done 3328 to go. Time: 4.7 hr. Time left: 56 sec of 4.7 hr.
....
999853 done 147 to go. Time: 4.7 hr. Time left: 2 sec of 4.7 hr.
999918 done 82 to go. Time: 4.7 hr. Time left: 1 sec of 4.7 hr.
999979 done 21 to go. Time: 4.7 hr. Time left: 0 sec of 4.7 hr.
```





One can also add a message to follows the print as

```julia
TS=TimingProgress(TS,n,NSamples,Message="My Message")
```

A print message could then look like

```
72 done 999928 to go. Time: 1 sec. Time left: 3.9 hr of 3.9 hr.
Accepted 26105 of 50880 => 51.306996855345915%
159 done 999841 to go. Time: 2 sec. Time left: 3.5 hr of 3.5 hr.
Accepted 40539 of 78720 => 51.49771341463415%
246 done 999754 to go. Time: 3 sec. Time left: 3.4 hr of 3.4 hr.
Accepted 54883 of 106560 => 51.50431681681682%
.....
```