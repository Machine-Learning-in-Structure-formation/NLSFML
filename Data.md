#Data Access

For our porpuse for analyzing the conditions and features of particles which end up into a halo dark matter at z = 0, we needed the data of particles in different snapshots.

Thus for this porpuse we used the Virgo-Millenium database.The simulation was carried out using a modiﬁed version of the publicly available code GADGET-2  (Springel 2005). The algorithm SUBFIND (Springel et al. 2001) was used to identify all self-bound halos containing at least 20 particles and all self-bound subhalos within these halos down to the same mass limit. 

A millenium run uses  uses 10^10 particles of mass 8.6×108 h^-1 * M_sun, to follow the evolution of the dark matter distribution within acubic region of side 500 h^−1 * Mpc from z = 127 (snapNumber = 67) until z = 0 (snapNumber = 0) . The cosmological parameters assumed are Ωm = Ωdm +Ωb = 0.25, Ωb = 0.045,  ΩΛ = 0.75, h = 0.73, σ8 = 0.9 and n = 1 with standard deﬁnitions for all quantities. 

In order to access the data we used the standard Structural Query Language(SQL). 
In our context an In-halo-particle at any redshift(z) is a sub-halo with mass between 1 to 100 m_particle ( which is equal to 8.6×108 h^-1 * M_sun) which will end up into a larger halo with the minimum mass of 1600 m_particle (means 1.4 * 10^12 h^-1 * M_sun) at z = 0. An out-halo-particle is visa versa is a sub-halo with masss betweeen 1 and 100 m_particle, which do not end up in a halo with a mass larger than the above limit at z=0 . 

So our task were visualizing the statistical data of these two different class of particles at different redshifts, and also to find and analyzing the data of density field at these redshifts.
We used the merger trees database to finding the history of each sub-halo. you can find more information about the merger trees in this link: http://gavo.mpa-garching.mpg.de/MyMillennium/Help?page=mergertrees.

We downloaded about 20 MB data in three different redshifts 16.7, 5.3, 2.4 including the velocity vectors, spatial indices, halo mass, and the last progenitors( see the merger trees) IDs.
we used these tables to access the data:

