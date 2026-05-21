---
layout: daily_post
title: Primeiro Daily
date: 2026-05-21
---
# When one chord is enough: estimating asteroid sizes from single-pass occultations

Morgado, **Fonseca**, Gomes-Júnior, Catani & Pereira · *AJ* 171:277 · [doi:10.3847/1538-3881/ae4fab](https://doi.org/10.3847/1538-3881/ae4fab)

Every so often, an asteroid drifts in front of a background star and snuffs out its light for a fraction of a second. Observers on the ground see the star blink off and back on, and from the duration of that blink they can measure a chord — a linear slice across the asteroid's silhouette. When dozens of stations observe the same event from different latitudes, the chords tile together into a precise 2D outline of the body. But here is the reality: out of 5,271 recorded stellar occultation events, roughly 81% yielded only a single chord. One station, one measurement, and no obvious way to extract a meaningful size.

Our paper asks whether those lone-chord events can be rescued for science. The answer is yes — if you treat the problem probabilistically. The key insight is geometric: if we assume the asteroid is roughly spherical and that the observer could have landed anywhere within the shadow swath (a fair assumption given ephemeris uncertainties), then the impact parameter — the perpendicular distance between the chord and the body's centre — is uniformly distributed. That uniform prior on geometry, combined with Bayes' theorem and a power-law prior on asteroid size distributions, turns a single chord length *L* into a full posterior distribution over possible radii.



The core likelihood

![](<div style="text-align:center; margin: 2rem 0;">   <img src="URL_DA_IMAGEM" style="width:80%; max-width:700px; height:auto;"> </div>)

The posterior P(R | L) ∝ P(L | R) · P(R), with P(R) ∝ R−2.5 as the size prior. The most probable radius is L/2 — the diametral case — with a skewed tail toward larger bodies (skewness ≈ 0.71). The 68% credible interval spans roughly ±9.5% of L; the 95% interval, ±32% of L.

![]()

![]()
