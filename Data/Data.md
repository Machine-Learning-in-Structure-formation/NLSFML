# Data Access

For our porpuse for analyzing the conditions and features of particles which end up into a halo dark matter at z = 0, we needed the data of particles in different snapshots.

Thus for this porpuse we used the Virgo-Millenium database.The simulation was carried out using a modiﬁed version of the publicly available code GADGET-2  (Springel 2005). The algorithm SUBFIND (Springel et al. 2001) was used to identify all self-bound halos containing at least 20 particles and all self-bound subhalos within these halos down to the same mass limit. 

A millenium run uses  uses 10^10 particles of mass 8.6×108 h^-1 * M_sun, to follow the evolution of the dark matter distribution within acubic region of side 500 h^−1 * Mpc from z = 127 (snapNumber = 67) until z = 0 (snapNumber = 0) . The cosmological parameters assumed are Ωm = Ωdm +Ωb = 0.25, Ωb = 0.045,  ΩΛ = 0.75, h = 0.73, σ8 = 0.9 and n = 1 with standard deﬁnitions for all quantities. 

In order to access the data we used the standard Structural Query Language(SQL). 
We derived our demanded data in two ways: 
First a data from merger trees database(http://gavo.mpa-garching.mpg.de/MyMillennium/Help?page=mergertrees) on the history of a given halo at a given redshift, at a bigger redshift. Which in this context we started to clasify our data in two groups, an In-halo-particle at any redshift(z) is a sub-halo with mass between 20 to 100 m_particle ( which is equal to 8.6 × 10^8 h^-1 * M_sun) which will end up into a larger halo with the minimum mass of 1600 m_particle (means 1.4 * 10^12 h^-1 * M_sun) at z = 0. An out-halo-particle is visa versa a sub-halo with mass between 20 and 100 m_particle, which do not end up in a halo with a mass larger than the above limit at z=0. we collected about 30MB data in 4 different snapshots (redshift) of this type. including  velocity vectors, spatial indices, halo mass, and the last progenitors( see the merger trees) IDs.
Second the particles data which contain all the data of a given particle at a given redshift. But as this data were quite large (about 1TB on the hole millinium run) and also in order to make a fair balance between accuracy of results and run-time (even run-time for our queries! which couldn't be more than 30 minute in each run), we forced to work on the "millimil" in place of the hole run. It contains the data of a 60*60*60 h^-1 * Mpc box with about 20 milion particles and 5 Kpc resolution. We collect about 5GB data of all particles in this box for 3 snapshots. Including the spatial indices and velocity vector of each particle.

Here is the general information about the related tables which millinium database contain, we used MPAHalo, MillimilSnapshotIDs and MillimiSnapshots for our purpose:
![](/Data/tables.PNG)

for making our in and out classes, we couldn't run an exact query for getting the information straight from the database because of gate open time limit, so we collected the information about all the particles which exist in a halo with np>1600 at z=0 and we traced these particles into z=127 by running a python code, you can find the code in the current ripository: https://github.com/Machine-Learning-in-Structure-formation/NLSFML/blob/master/Data/IN_OUT_Halo_Particles.ipynb

also we uploaded a sample of our created data about particles in their IN-OUT-halo information, which you can find it as a compress file here:

unfortunatlly uploading the full data isn't possible, because of it large size. 
# Simple analysis of Data

In order to visualize our data we plot some histograms which you can see as follows.

Halo Mass histogram:
we defined our halo class in a way that the minimum mass for a halo is equal to 1600 particles. as can be seen in the plot below, the number of halos with mass less than 10000 particles is much more than the bigger ones, as we expected from our cosmology. Total number of halos with np more than 1600 is also 706, while the total number of halos in the box (including the lighter ones) is around 37000.
![](/Data/Histogram_of_halo_masses.png)

The spatial distribution of particles in the millimil box for snapshot 63 
![](/Data/Particles_distribution_in_space_at_z%3D0.png)
![](/Data/Snap63_1.9m_particles_spatial_distribution.PNG)

snapshot 10:

snapshot 0:


# Aknowledgements

On a millenium run: https://arxiv.org/abs/astro-ph/0608019

Springel, V . (2005), The cosmological simulation code GADGET-2, Mon. Not. R. Astron. Soc., 364, 1105 
