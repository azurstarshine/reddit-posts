Slower, yes, but I run into myself occasionally, *long* before I come anywhere near running out of oil. I just now ran into it and have over 12000 oil available. I also ran into it last night, and I went back over my oil cap over night. I've [done some math before](/r/AzurLane/comments/10i59jg/comment/j5e43g7/), but let's update it with better formatting and a slightly different approach.

Instead of battles, we'll look at entire runs. So the equation becomes:

$$0 = m_i + m_{recover} t - m_{run} r t$$

where

* $m_i$ is the initial morale
* $m_{recover}$ is the morale recovery per hour
* $m_{run}$ is the morale used per run
* $r$ is the number of runs per hour
* $t$ is the time

Solving for $t$:

$$
\begin{aligned}
0 &= m_i + (m_{recover} - m_{run} r) t \\\\
- (m_{recover} - m_{run} r) t &= m_i \\\\
(m_{run} r - m_{recover}) t &= m_i \\\\
t &= \frac{m_i}{m_{run} r - m_{recover}}
\end{aligned}
$$

I like to sanity check with my units.

$$\frac{\mathrm{morale}}{(\frac{\mathrm{morale}}{\mathrm{run}}) (\frac{\mathrm{runs}}{\mathrm{hour}}) - (\frac{\mathrm{morale}}{\mathrm{hour}})}$$
$$\frac{\mathrm{morale}}{(\frac{\mathrm{morale}}{\mathrm{hour}}) - (\frac{\mathrm{morale}}{\mathrm{hour}})}$$
$$\frac{\mathrm{morale}}{(\frac{\mathrm{morale}}{\mathrm{hour}})}$$
$$\mathrm{morale} \left( \frac{\mathrm{hour}}{\mathrm{morale}} \right) $$
$$\mathrm{hours}$$

So we have $t$ is in $\mathrm{hours}$. That checks out.

# Values

## Initial morale

$$m_i = 150 \ \mathrm{morale}$$

## Recovery

We'll compute for two different values:

* $m_{recover} = 40 \ \frac{\mathrm{morale}}{\mathrm{hour}}$ for an unoathed ship in the downstairs dorm
* $m_{recover} = 50 \ \frac{\mathrm{morale}}{\mathrm{hour}}$ for an unoathed ship in the upstairs dorm

## Morale consumed per run

Obviously, we're only interested in the mob fleet, since it will run out long before the boss fleet's. The boss fleet may even have time to fully recover their lost morale between battles.

A run of T5 takes 6 mob battles. A normal battle consumes 2 morale per battle, but using the HECLP doubles it to 4 per battle. We'll compute with both values:

* $m_{run} = 6 \ \frac{\mathrm{battles}}{\mathrm{run}} * 2 \ \frac{\mathrm{morale}}{\mathrm{battle}} = 12 \ \frac{\mathrm{morale}}{\mathrm{run}}$ for a normal run
* $m_{run} = 6 \ \frac{\mathrm{battles}}{\mathrm{run}} * 4 \ \frac{\mathrm{morale}}{\mathrm{battle}} = 24 \ \frac{\mathrm{morale}}{\mathrm{run}}$ for an HECLP run

## Number of runs per hour

This is obviously the biggest variable. How many full runs can you do per hour? You have a lot of factors to consider: 7 battles, a screen load per battle, the actual battle, time to move between nodes each battle, time to restart a new run during Auto-Repeat, time to notice the Auto-Repeat has ended, and time to clear out your dock of ship drops between Auto-Repeats before starting off a new one. It's hard to get an exact number here, but let's just think about it a little. 2 full Auto-Repeats per hour actually sounds kind of slow. That's a full half hour for that whole process. On the other hand, 3 full Auto-Repeats per hour might be pushing things a little; that only gives you 20 minutes for a full run and everything between, including time to notice. You'd have to have a battle load and complete the battle in less than a minute because $ (7 \ \mathrm{battles})(1 \ \frac{\mathrm{battle}}{\mathrm{minute}}) = 21 \mathrm{minutes} $. 2 Auto-Repeats is 6 runs, and 3 Auto-Repeats is 9 runs. So let's try the values between those two:

* $r = 7 \ \frac{\mathrm{runs}}{\mathrm{hour}}$
* $r = 8 \ \frac{\mathrm{runs}}{\mathrm{hour}}$

These of course represent partial Auto-Repeats, but that's fine. We're not going to get exact numbers here, anyway. We just want to see what time frames pop out to get a rough idea of whether running out of morale is feasible.

# Example

We're going to have 8 different results to compare, and I don't want to show manually working through the math with all of them. So here's an example of actually doing the computation once with $m_{recover} = 40 \ \frac{\mathrm{morale}}{\mathrm{hour}}$, $m_{run} = 12 \ \frac{\mathrm{morale}}{\mathrm{run}}$, and $r = 7 \ \frac{\mathrm{runs}}{\mathrm{hour}}$:

$$
\begin{aligned}
t &= \frac{m_i}{m_{run} r - m_{recover}} \\
t &= \frac{150 \ \mathrm{morale}}{(12 \ \frac{\mathrm{morale}}{\mathrm{run}}) (7 \ \frac{\mathrm{runs}}{\mathrm{hour}}) - (40 \ \frac{\mathrm{morale}}{\mathrm{hour}})} \\
t &= \frac{150 \ \mathrm{morale}}{(84 \ \frac{\mathrm{morale}}{\mathrm{hour}}) - (40 \ \frac{\mathrm{morale}}{\mathrm{hour}})} \\
t &= \frac{150 \ \mathrm{morale}}{44 \ \frac{\mathrm{morale}}{\mathrm{hour}}}
t &= \frac{150}{44} \mathrm{hours} \\
t &= 3 \frac{9}{22} \mathrm{hours} & \approx 3 \mathrm{hours} \, 24.55 \mathrm{minutes}
\end{aligned}
$$

So in this case, you can farm for almost 3.5 hours before you run out of morale, and this is the lower end of the values we're looking at.

# Results

Running the computation for *all* of the values mentioned before gives us these results.

First we look at running without an HECLP, which corresponds to $m_{run} = 12 \ \frac{\mathrm{morale}}{\mathrm{run}}$.

| $r \overset{\large\setminus}{}\overset{\large m_{recover}}{}$ | 40 | 50 |
|-|-|-|
| 7 | $3.409091 \ \mathrm{hours} \approx 3 \ \mathrm{hours} \ 24.5 \ \mathrm{minutes}$ | $4.411765 \ \mathrm{hours} \approx 4 \ \mathrm{hours} \ 24.7 \ \mathrm{minutes}$ |
| 8 | $2.678571 \ \mathrm{hours} \approx 2 \ \mathrm{hours} \ 40.7 \ \mathrm{minutes}$ | $3.26087 \ \mathrm{hours} \approx 3 \ \mathrm{hours} \ 15.7 \ \mathrm{minutes}$ |

As we can see, even in this case, it only takes a couple of hours of consistently firing off an Auto-Repeat. That's not hard to do if you're doing something that lets you keep an eye on the game. Some players might also leverage notifications, although I don't know much about that because I have them disabled.

Second, we look at running with an HECLP, which uses $m_{run} = 24 \ \frac{\mathrm{morale}}{\mathrm{run}}$.

| $r \overset{\large\setminus}{}\overset{\large m_{recover}}{}$ | 40 | 50 |
|-|-|-|
| 7 | $1.171875 \ \mathrm{hours} \approx 1 \ \mathrm{hour} \ 10.3 \ \mathrm{minutes}$ | $1.271186 \ \mathrm{hours} \approx 1 \ \mathrm{hour} \ 16.3 \ \mathrm{minutes}$ |
| 8 | $0.986842 \ \mathrm{hours} \approx 0 \ \mathrm{hours} \ 59.2 \ \mathrm{minutes}$ | $1.056338 \ \mathrm{hours} \approx 1 \ \mathrm{hour} \ 3.4 \ \mathrm{minutes}$ |

In this case, we can barely get over an hour of grinding in.

# Oil

With oil caps, T5 uses 160 oil per run. A full Auto-Repeat uses 480 oil. In the longest case, $7 \ \frac{\mathrm{runs}}{\mathrm{hour}}$ for almost 4.5 hours, we're looking at 31.5 runs. That's uses 5040 oil. For the shortest case, we're only looking at 8 runs at double oil, using 2560 oil. So you can definitely run out of morale well before oil.
