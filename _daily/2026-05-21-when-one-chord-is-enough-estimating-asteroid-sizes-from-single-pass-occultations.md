---
layout: daily_post
title: "When one chord is enough: estimating asteroid sizes from single-pass
  occultations"
date: 2026-05-21
---

---
title: Probabilistic Estimation of Asteroid Sizes from Single-chord Stellar Occultations
journal: The Astronomical Journal
citation: Morgado, Fonseca, Gomes-Júnior, Catani & Pereira — AJ 171:277 (2026)
draft: false
---
 
*Morgado, **Fonseca**, Gomes-Júnior, Catani & Pereira · The Astronomical Journal 171:277 · [doi:10.3847/1538-3881/ae4fab](https://doi.org/10.3847/1538-3881/ae4fab)*
 
---
Every so often, an asteroid drifts in front of a background star and briefly blocks its light. Observers on the ground see the star blink off and back on, and from the duration of that blink they can measure a chord, a linear slice across the asteroid's silhouette. When dozens of stations observe the same event from different latitudes, the chords combine into a detailed 2D outline of the body. But here is the reality: out of 5,271 recorded stellar occultation events, roughly 81% yielded only a single chord. One station, one measurement, and no obvious way to extract a meaningful size.

Our paper asks whether those lone-chord events can still be scientifically useful. The answer is yes, if the problem is treated probabilistically. The key insight is geometric: a short observed chord does not necessarily imply a small asteroid. The observer may simply have crossed near the edge of a much larger shadow. By combining geometric reasoning, Bayesian inference, and known asteroid size distributions, a single occultation measurement can be transformed into a full probability distribution over possible asteroid radii.

## The core idea

Instead of reconstructing the asteroid shape directly, the method estimates how likely different radii are given the observed chord. The most probable solution corresponds to the diametral case, where the observer crosses near the centre of the object, but the probability distribution naturally extends toward larger bodies as well. This produces asymmetric credible intervals rather than a single deterministic value.

Chord-length uncertainty is incorporated directly into the statistical model, which suppresses unrealistic large-radius solutions and yields more physically meaningful intervals. More importantly, independent single-chord events from different epochs can be combined together statistically, allowing the uncertainty to shrink substantially over time. With five independent observations, the radius estimate becomes dramatically more constrained.

## Key numbers

| Metric | Value |
|---|---|
| Single-chord radius uncertainty (one event) | ~10% |
| Total events in public database | 5,271 (81% single-chord) |
| 95% retrieval rate, single chord | 84.7% (100k Monte Carlo simulations) |
| TNOs expected from LSST | >30,000 |

## Validation across morphologies

We validated the method on well-characterised solar system bodies spanning a wide morphological range: nearly spherical dwarf planets such as Ceres and Vesta, moderately irregular main-belt asteroids such as Pallas and Juno, the elongated bone-shaped Kleopatra, and the contact-binary Arrokoth visited by New Horizons. For spherical and moderately irregular bodies, the recovered radii remain consistent with values obtained from spacecraft imaging, radar, and adaptive optics observations.(!!!) Even for strongly non-spherical objects, the method still retrieves effective equivalent radii within realistic ranges.

## Why now? Hehehe

The timing of this work is not coincidental. The Vera C. Rubin Observatory's Legacy Survey of Space and Time (LSST) is beginning operations and is expected to discover more than 30,000 trans-Neptunian objects. Combined with Gaia's precise stellar positions, the number of predicted occultations will increase dramatically. Most newly discovered objects will initially be observed through isolated single-chord events long before coordinated multi-station campaigns become possible.

Our framework offers a statistically principled way to extract scientifically useful size estimates from those observations. Instead of discarding single-chord occultations as incomplete measurements, they can become valuable constraints for thermal modelling, population studies, and the large-scale statistical characterisation of the outer Solar System.

The primary caveat is the circular-shape assumption. Highly elongated or bilobed bodies will yield effective equivalent radii rather than exact axis dimensions. Extending the framework to ellipsoidal shape priors is a natural direction for future work.
