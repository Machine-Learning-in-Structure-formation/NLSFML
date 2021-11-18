# 0 - Machine learning in non linear structure formation
Machine learning methods in investigating the Halo Dark matter formation.
Full description of project in the termpaper report: [Reprot part1]()
# 1 - Data Access

For our porpuse for analyzing the conditions and features of particles which end up into a halo dark matter at z = 0, we needed the data of particles in different snapshots. Also we needed a unique ID for all the particles during the whole run, which would let us to trace back particles in time. And this is the reason that find Millenium database appropriate for our project. (in comparison with other datasets like [IllustrisTNG](https://www.tng-project.org/data/) )

We used the [Virgo-Millenium database](https://wwwmpa.mpa-garching.mpg.de/millennium/).The simulation was carried out using a modiﬁed version of the publicly available code GADGET-2  (Springel 2005). The algorithm SUBFIND (Springel et al. 2001) was used to identify all self-bound halos containing at least 20 particles and all self-bound subhalos within these halos down to the same mass limit. 

A millenium run uses 10^10 particles of mass 8.6×108 h^-1 * M_sun, to follow the evolution of the dark matter distribution within a cubic region of sides 500 h^−1 Mpc from z = 127 (snapNumber = 0) until z = 0 (snapNumber = 63) . The cosmological parameters assumed are Ωm = Ωdm +Ωb = 0.25, Ωb = 0.045,  ΩΛ = 0.75, h = 0.73, σ8 = 0.9 and n = 1 with standard deﬁnitions for all quantities. 

In order to access the data we used the standard Structural Query Language(SQL).
***You can find a much expanded description about Millinium run and our queries in [our report](https://github.com/Machine-Learning-in-Structure-formation/NLSFML/blob/master/Data/ML_Project_Part_1_Data.pdf).***
 
We derived our demanded data in two ways: 
First a data from [merger trees database](http://gavo.mpa-garching.mpg.de/MyMillennium/Help?page=mergertrees) on the history of a given halo at a given redshift. Which in this context we started to clasify our data in two groups in a special way, an In-halo-particle at any redshift(z) is a sub-halo with mass between 20 to 100 m_particle ( equal to 8.6 × 10^8 h^-1 * M_sun) which will end up into a larger halo with the minimum mass of 1600 m_particle (means 1.4 * 10^12 h^-1 * M_sun) at z = 0. An out-halo-particle is visa versa a sub-halo with mass between 20 and 100 m_particle, which do not end up in a halo with a mass larger than the above limit at z=0. we collected about 30MB data in 4 different snapshots (redshift) of this type. including  velocity vectors, spatial indices, halo mass, and the last progenitor(see the merger trees) IDs.

Second the particles data which contain all the data of a given particle at a given redshift. But as this data were quite large (about 1TB on the hole millinium run) and also in order to make a fair balance between accuracy of results and run-time (even run-time for our queries! which couldn't be more than 30 minute in each run), we forced to work on the "millimil" in place of the hole run. It contains the data of a 60*60*60 (h^-1 Mpc)^3 box with about 20 milion particles and 5 Kpc resolution. We collected about 5GB data of all particles in this box for 3 snapshots. Including the spatial indices and velocity vectors of each particle.

[A short report of the used queries.](https://github.com/Machine-Learning-in-Structure-formation/NLSFML/blob/master/Data/Queries.txt)

Here is the general information about the related tables which millinium database contain, we used MPAHalo, MillimilSnapshotIDs and MillimiSnapshots for our purpose:

![](/Data/tables.PNG)

Now we are ready to analyse our data and create our appropriate classes, you can find our complete notebook [here.](https://github.com/Machine-Learning-in-Structure-formation/NLSFML/blob/master/Data/Full_codes_plots.ipynb)

**The list of contained codes in the [Notebook](https://github.com/Machine-Learning-in-Structure-formation/NLSFML/blob/master/Data/Full_codes_plots.ipynb)**:

1-Visualizing and generating IN and OUT class particles in z=127 to get better understanding of effective features

2-Halo mass histogram in z=0 and making IN and OUT classes

3-Particles spatial distribution for different snapshots

4-Particles velocity distribution for different snapshots

**Also you can find a sample of the finalized data [here.](https://github.com/Machine-Learning-in-Structure-formation/NLSFML/tree/master/Data/Data_Sample)** 
unfortunatlly uploading the full data isn't possible, because of it's large size.

# - Aknowledgements

On a millenium run: https://arxiv.org/abs/astro-ph/0608019

Springel, V . (2005), The cosmological simulation code GADGET-2, Mon. Not. R. Astron. Soc., 364, 1105: https://wwwmpa.mpa-garching.mpg.de/gadget/

Machine learning cosmological structure formation: https://arxiv.org/abs/1802.04271

Andrew Pontzen Luisa Lucie-Smith Hiranya V. Peiris. “An interpretable machine learning framework for dark matter halo formation”. In: (2019). url: https://arxiv.org/abs/1906.06339. 

Andrew R. Zentner. “The Excursion Set Theory of Halo Mass Functions, Halo Clustering, and Halo Growth”. In: (2006). url: https://arxiv.org/ abs/astro-ph/0611454.

