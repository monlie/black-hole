### Ray-traced simulation of a black hole

_see **[COPYRIGHT.md](https://github.com/oseiskar/black-hole/blob/master/COPYRIGHT.md)** for license and copyright info_

In this simulation, the light ray paths are computed by integrating an ODE describing the Schwarzschild geodesics (see [this page the maths](https://github.com/oseiskar/black-hole/blob/numeric-notebooks/physics.ipynb)) using GLSL on the GPU, leveraging WebGL and [three.js](http://threejs.org). This should result to a fairly physically accurate gravitational lensing effect. Various other relativistic effects have also been added and their contributions can be toggled from the GUI.

The simulation needs a decent GPU and recent variant of Chrome or Firefox to run smoothly. Frame rate can be increased by shrinking the browser window and/or reducing screen resolution.

**Known artefacts**

 * The striped accretion disk and planet textures are (obviously?) fake and are included to help visualizing motion.
 * The spectrum used in modeling the doppler shift of the Milky Way background image is quite arbitrary (not based on real spectral data) and consequently the doppler-shifted background colors may be wrong.
 * There is a "blind spot" solver artefact when looking away from the black hole.
 * The light paths bend a bit more than they should due to low ODE solver step counts (see [numeric tests](https://github.com/oseiskar/black-hole/blob/numeric-notebooks/numeric_tests.ipynb)), but this seems to happen in a systematic way so that the image looks very similar in comparison to a more accurate simulation.
 * The step sizes are changed when toggling "gravitational time dilation", resulting to noticeable changes in the numerical artefacts. The "real" Shapiro delay effect is noticeable as apparent shearing of the planet when moving it very close to the black hole and viewing it from above.
 * Lorentz contraction causes jagged looks in the planet when simultaneously enabled with "light travel time" and the planet is close to the black hole.
 * Texture sampling issues cause unintended star blinking
