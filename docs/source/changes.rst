Changelog
=========

All notable changes to this project will be documented in this file.

[unreleased - most recent changes come first]
---------------------------------------------

🚀 Features
~~~~~~~~~~

-  Lower down the exhaustiveness as it takes unecessarily long. -
   (`dbb8aae <https://github.com/Isra3l/MolSanitizer/commit/dbb8aaeb1d9ba8450f7221ecc9f69817d163990a>`__)
-  Now support enrichment mode, not putting the db2 files into db2.tgz.
   Maily for adapting with the internal enrichment pipeline. -
   (`004af69 <https://github.com/Isra3l/MolSanitizer/commit/004af6938faef4507ee9c32f7229e78471e73b88>`__)
-  Trial of new stochastic sampling method that involved in increased
   sampling but keeping the failure count continously increase without
   being resetted after every good conformer. This shown a 2X
   performance on a small tricky subset. -
   (`b5f8e32 <https://github.com/Isra3l/MolSanitizer/commit/b5f8e32d1608dc9de3e8ca7be67014f6e7691465>`__)
-  SMILES is now back to the DB2 format! -
   (`0da0468 <https://github.com/Isra3l/MolSanitizer/commit/0da04682d7cea4588945ee4fddaf5e8f1fb4ff16>`__)
-  New implementation of stochastic sampling that can sample more
   exhaustively the conformational space. This involves sampling more
   and filter later at the end. Msani now doesn’t write out and read in
   intermediate files repeatedly but process in the memory to speed up
   the process. -
   (`6edbfad <https://github.com/Isra3l/MolSanitizer/commit/6edbfadda576db3c4b819e88aa7881615fb84847>`__)
-  The default maximum stereoisomers to be expanded is now set to 8
   (previously 32). This could always be set specifically by flag
   –max_isomers. -
   (`536f5fe <https://github.com/Isra3l/MolSanitizer/commit/536f5fe94af181e32a9d5b3ad7d54f11061b61df>`__)
-  Log files and input files now being organized to corresponding
   folders. New cleanup mechanism for msani_batch. -
   (`16c7f11 <https://github.com/Isra3l/MolSanitizer/commit/16c7f111b43f67c7ec3b60844f89723a55180382>`__)
-  DB2 files now are put in tar.gz by default. The number of files in
   each tar.gz depends on the number of lines per job. -
   (`dbd74a4 <https://github.com/Isra3l/MolSanitizer/commit/dbd74a42537fed8c4e123f1f255b3debbd57d958>`__)

🐛 Bug Fixes
~~~~~~~~~~~

-  The recent increased sampling seems to run too long on some case
   examples. This was the case of very flexbile but contain multiple
   repulsive parts. The current implementation should sampling faster
   for these cases. -
   (`aed5d98 <https://github.com/Isra3l/MolSanitizer/commit/aed5d98369b116d8a084b01b8cd735802a45e2d7>`__)
-  Fix a bug inheriting from the recent mol2 implementation improvement.
   Mol2 objects are now deepcopy to avoid referencing issues. -
   (`58a0815 <https://github.com/Isra3l/MolSanitizer/commit/58a081580eea581081b963e6b4512553a2a7eeac>`__)
-  Constraints to MMFF94s to make the N atoms in amide linkages planar.
   -
   (`f1f82b7 <https://github.com/Isra3l/MolSanitizer/commit/f1f82b7b7705b1bb5e32a3624fa7890e49b5a773>`__)

🚜 Refactor
~~~~~~~~~~

-  Refactor the organization of the Mol2 object. -
   (`77b6fed <https://github.com/Isra3l/MolSanitizer/commit/77b6fed73721a91ff569e1808fba73e7ac03b6fe>`__)
-  Remove deprecated scripts. -
   (`4d82dfa <https://github.com/Isra3l/MolSanitizer/commit/4d82dfa97a7bf0adb6a11f3c7d6656ad3cd12329>`__)
-  Remove deprecated scripts. -
   (`80f915c <https://github.com/Isra3l/MolSanitizer/commit/80f915c7187d7d2b7b089f2885765b0f4d85c893>`__)
-  Remove deprecated script that is not used anymore. -
   (`3cfa3b8 <https://github.com/Isra3l/MolSanitizer/commit/3cfa3b87c545e416eee007c0ca643b3a27e21246>`__)

📚 Documentation
~~~~~~~~~~~~~~~

-  Redirect MolSanitizer README to the read-the-docs page. -
   (`6e6bc43 <https://github.com/Isra3l/MolSanitizer/commit/6e6bc434bc69180c67b24950fb476b21898907ea>`__)

⚡ Performance
~~~~~~~~~~~~~

-  Modifications to mol2db2 allows the mol2 object being recorded
   on-the-fly rather than reading from the mol2 blocks. OpenBabel is now
   only being used for the initial conversion for AMSOL. -
   (`65eed12 <https://github.com/Isra3l/MolSanitizer/commit/65eed12479d9d31fc11eeb31d0b40061f59fab5a>`__)

🎨 Styling
~~~~~~~~~

-  Solv files are now deleted even the nocleanup is used. The .solv file
   is still exist in the db2 folder if the user want to check for the
   partial charges and desolvation penalties. -
   (`b99efdf <https://github.com/Isra3l/MolSanitizer/commit/b99efdf80ef94561b591f4b8bbd4bb107c33e8e8>`__)

[0.2.0] - 2024-11-06
--------------------

.. _features-1:

🚀 Features
~~~~~~~~~~

-  Updated new rules for aromatic hydroxyls to make them coplanar with
   the aromatic rings. -
   (`b240a29 <https://github.com/Isra3l/MolSanitizer/commit/b240a29fd03dde6ccd64da19dc1a7b79f86d7f0e>`__)
-  Initial implementation of OpenBabel 3D embedding for faster initial
   embedding process. Set the default timeout to 2 minutes as surveyed
   from the Tetralith clusters. -
   (`056270f <https://github.com/Isra3l/MolSanitizer/commit/056270f5acb1205d84e10a81b87824e9fba80cf6>`__)
-  New default energywindow is 25 kcal/mol as we found that this window
   could compromise the accuracy in terms of both redocking and
   enrichment. -
   (`2241d1a <https://github.com/Isra3l/MolSanitizer/commit/2241d1a0f34bdc7ec480f7b641c09adebdd14cb4>`__)
-  Implemented parallelization for tautomers and stereoisomers options -
   (`5996a32 <https://github.com/Isra3l/MolSanitizer/commit/5996a3231cca650daa44fbe834fb8c9bceb80f5e>`__)
-  Improved the initial conformations of conjugated Ns in heterocyclics
   inherited from using MMFF94s forcefield. Now these heterocycles
   should be planar. -
   (`3660f8b <https://github.com/Isra3l/MolSanitizer/commit/3660f8b30fdb1ca59bda1b24e2bf8f6f8f425b47>`__)
-  New mechanism of running AMSOL to avoid shell piping issues. -
   (`78f2176 <https://github.com/Isra3l/MolSanitizer/commit/78f2176fd9c3c715ac9a6864a8a0ebbc0a55ce5c>`__)
-  New mechanism of calculating maximum possible stereoisomers based on
   unassigned chiral centers -
   (`142a3f6 <https://github.com/Isra3l/MolSanitizer/commit/142a3f6ff7ab51e25455a069aaba6e7d8566d7ca>`__)
-  New cleanup method to support non-SLURM jobs -
   (`c89e127 <https://github.com/Isra3l/MolSanitizer/commit/c89e127a5b301ce12c90311cf281b2aa82af86dd>`__)
-  Msani now supports the multithreading for stereoisomers enumeration
   and set the time out for this process for each entry to 1 minute
   only. -
   (`d5d4c9e <https://github.com/Isra3l/MolSanitizer/commit/d5d4c9e7957ec31b386204894ef91d7b81285943>`__)
-  Msani now only allows up to 4 minutes in the initial embedding stage.
   This is to avoid compounds that take too long for embedding that are
   likely because of the error in the SMILES level. -
   (`7c66150 <https://github.com/Isra3l/MolSanitizer/commit/7c6615084d948b6e2f2e362e8fc7d421ba7c2fdc>`__)
-  MolSanitizer now suggests the user to update rdkit to avoid known
   errors with stereoisomers and tautomers. -
   (`63750b3 <https://github.com/Isra3l/MolSanitizer/commit/63750b3d52f3b12ac3a85f44ec7c1bfae015f2ae>`__)

.. _bug-fixes-1:

🐛 Bug Fixes
~~~~~~~~~~~

-  Fix a bug in run_amsol that makes msani proceed although AMSOL
   failed. -
   (`ec4210c <https://github.com/Isra3l/MolSanitizer/commit/ec4210cb76969f2cb021bd689893d954120f54d1>`__)
-  Fix a bug that the DB2 file loses the information about the input
   names -> make all the DB2 files have the same name as \****\* -
   (`755d696 <https://github.com/Isra3l/MolSanitizer/commit/755d69641b1eb5df29a70b9d569e3b3a9c3f94d1>`__)

.. _refactor-1:

🚜 Refactor
~~~~~~~~~~

-  Remove deprecated functions -
   (`9bc63b6 <https://github.com/Isra3l/MolSanitizer/commit/9bc63b6fde4568f4e83a67823fe0177110cf4773>`__)

.. _section-1:

[0.1.3] - 2024-10-05
--------------------

.. _features-2:

🚀 Features
~~~~~~~~~~

-  MolSanitizer now will skip generating DB2 file if the file already
   exist. -
   (`52d7a40 <https://github.com/Isra3l/MolSanitizer/commit/52d7a4044d03276993b1e6061309f110d09606d4>`__)
-  Warn the user if not all the stereoisomers are written out. -
   (`1e56118 <https://github.com/Isra3l/MolSanitizer/commit/1e561180b912a98af541163c07af701a011aea2e>`__)
-  New default values of energywindow=15 and max_isomers=32 (max
   stereoisomers to be enumerated) -
   (`d901665 <https://github.com/Isra3l/MolSanitizer/commit/d901665b804bfb5e7fd0842b08731e7f6e483c38>`__)
-  :bug: New cleanup mechanism for sessions not running in a SLURM job.
   -
   (`2ae700a <https://github.com/Isra3l/MolSanitizer/commit/2ae700a19d9141e15b9371f77a4fb8418ba5b6cf>`__)
-  Only commit CHANGELOG.md when CHANGELOG.md contains differences. -
   (`5f87498 <https://github.com/Isra3l/MolSanitizer/commit/5f87498b2854b657766719a6a18162ad4ea97acd>`__)
-  New msani_batch interface, showing the user how many jobs prior to
   submission. -
   (`fcd9755 <https://github.com/Isra3l/MolSanitizer/commit/fcd9755fc37a971785091defa73232fd3171a2d6>`__)
-  :bug: Update new stereoisomers and tautomers expansion name patterns.
   -
   (`239b92a <https://github.com/Isra3l/MolSanitizer/commit/239b92aecf9f2146c151e0dab0d4ec0b9ec48133>`__)
-  New alignment rules for non-ring compounds -
   (`c2376ac <https://github.com/Isra3l/MolSanitizer/commit/c2376acd3eb9c75e01787fa9d70c352c660e4907>`__)
-  Reduced sampling for non-ring-containing molecules to mimic the
   behavior of DB2Pipeline. -
   (`5c55c43 <https://github.com/Isra3l/MolSanitizer/commit/5c55c433eb48cbbc77781758785105d727fef08a>`__)
-  New cleanup mechanism updated -
   (`727c5b6 <https://github.com/Isra3l/MolSanitizer/commit/727c5b6c60c530da062b784a35e122f042417b82>`__)
-  New cleanup mechanism so one job should not interfere other parallel
   jobs (on SLURM system). -
   (`fbfe34a <https://github.com/Isra3l/MolSanitizer/commit/fbfe34ab2c92a4d3d3b0f124c11a2498ccaca66f>`__)
-  Implementation of energy calculation for conformers and use
   energywindow to remove unfavorable conformers. -
   (`6fc4242 <https://github.com/Isra3l/MolSanitizer/commit/6fc4242d83293dd18ba4456bc05a7526f4da6a7a>`__)
-  Added the new parameter: energywindow to avoid unreasonable
   conformations -
   (`658d08c <https://github.com/Isra3l/MolSanitizer/commit/658d08ce81b9f8d25c530b6063bffb3d0f8388ad>`__)

.. _bug-fixes-2:

🐛 Bug Fixes
~~~~~~~~~~~

-  New cleanup mechanism, which should now cleanup even with parallel
   jobs of different array_id being running simultaneously. -
   (`0bb2bc9 <https://github.com/Isra3l/MolSanitizer/commit/0bb2bc9896907c3903425d11238429cdabd3fe68>`__)
-  Fix a bug in stereoisomers expansion -
   (`8f530c1 <https://github.com/Isra3l/MolSanitizer/commit/8f530c1ee8bea97589514c48d1c077874805a863>`__)
-  Compounds that fail to tautomerize should not interrupt the whole
   msani for now. If error in generating stereoisomers or tautomers
   occurs, the smiles should be kept as input rather than skipping it in
   the earlier version. -
   (`e17a0a1 <https://github.com/Isra3l/MolSanitizer/commit/e17a0a13189a3c17fcf0faf3000fd932e46dfc75>`__)

.. _refactor-2:

🚜 Refactor
~~~~~~~~~~

-  Remove unused codes -
   (`8437f18 <https://github.com/Isra3l/MolSanitizer/commit/8437f18d4afe59d018dc6b7d7a04f7e659898a1b>`__)

.. _section-2:

[0.1.2] - 2024-09-26
--------------------

.. _features-3:

🚀 Features
~~~~~~~~~~

-  Msani not use the reset terminal hydrogen of mol2db2 anymore. -
   (`f4d2d6e <https://github.com/Isra3l/MolSanitizer/commit/f4d2d6ec6b870f6a24fe4960c3622d983151de04>`__)

.. _bug-fixes-3:

🐛 Bug Fixes
~~~~~~~~~~~

-  The enumerated stereoisomers in the db2 part should also be output to
   the \_clean.smi file. -
   (`1c12e74 <https://github.com/Isra3l/MolSanitizer/commit/1c12e749b211869ca2b91267adde3906884e6251>`__)
-  Disable the default clash checking of mol2db2 program, which could
   make DOCK skips the potential conformations (msani already checked in
   the torsional sampling part). -
   (`09553b3 <https://github.com/Isra3l/MolSanitizer/commit/09553b388f5567f22461360383aa1cbd96af55e3>`__)
-  Unspecified stereocenters now will be enumerated automatically before
   undergoing conformational embedding. -
   (`e04b6d6 <https://github.com/Isra3l/MolSanitizer/commit/e04b6d6ff08692ad7c1f31d9fce1899531c81ac5>`__)
-  Fix a bug that generated compounds not containing the name -
   (`8618524 <https://github.com/Isra3l/MolSanitizer/commit/86185246b4c3ba090ab5e6d08bdc0153a4a6b1de>`__)
-  Try to fix the weird behavior of SLURM where all the entries failed
   (worked with flag –debug) -
   (`069cf1f <https://github.com/Isra3l/MolSanitizer/commit/069cf1f50736163512f3c4b2777d7595b8cab1a0>`__)
-  Failed initial embedding should not crash the whole session. -
   (`66c818b <https://github.com/Isra3l/MolSanitizer/commit/66c818b88c7479d5e55d2ee20fada5cee9c03b02>`__)
-  Fix another bug so that the compounds with no Torlib-satisfied
   conformation should output at least one conformation (from rdkit). -
   (`d71ff37 <https://github.com/Isra3l/MolSanitizer/commit/d71ff37cb3e94234edefbcdfc1f9d1786811b6a1>`__)
-  Fix a bug that make the molecules without any rotatable bonds failed
   to generate DB2 files. -
   (`4b0d04b <https://github.com/Isra3l/MolSanitizer/commit/4b0d04b56ef7b87a7c799688dcc0201655c15d2f>`__)

.. _refactor-3:

🚜 Refactor
~~~~~~~~~~

-  Make the script more pythonic, to avoid the speed inconsistent
   between subprocess and os/shutil of python. -
   (`db778dd <https://github.com/Isra3l/MolSanitizer/commit/db778dd4ca7ab6fd75c488e14640eadc1c2cae6a>`__)
-  Rewrite the main script (molSanitizer.py) to increase readability and
   better timing logging. -
   (`225590d <https://github.com/Isra3l/MolSanitizer/commit/225590da8d4a62f2b05366e077f935e60cc5f7ef>`__)
-  Refactor the script a little bit. Change rigid_part_rules so at least
   three atoms are matched. -
   (`e060c5a <https://github.com/Isra3l/MolSanitizer/commit/e060c5aef3bae4e3bb2e259eba901d4232a25ebb>`__)

.. _section-3:

[0.1.1] - 2024-09-22
--------------------

.. _features-4:

🚀 Features
~~~~~~~~~~

-  The msani_batch now allows setting up default settings using a yaml
   file (batch_configurations.yaml). -
   (`b2badad <https://github.com/Isra3l/MolSanitizer/commit/b2badad1efad59673e41e9a9ee714824653a712d>`__)
-  Set initial embeddings to 100 to save time and computational cost -
   (`6e1a8b2 <https://github.com/Isra3l/MolSanitizer/commit/6e1a8b234c7bb9ff689d9760d63817ce489c00be>`__)
-  Trial of using different alignment references and trial of 200
   initial conformations -
   (`ba4b8a1 <https://github.com/Isra3l/MolSanitizer/commit/ba4b8a120fec799572e4fff6ec2c84aadc375fa2>`__)
-  Trial of using smaller initial embedding to speed up the process -
   (`85cf8e1 <https://github.com/Isra3l/MolSanitizer/commit/85cf8e1e8a7c722e94f78d214fe022b93c5aa9c7>`__)
-  Trial of using smaller num_confs_ring (1 instead of 10) -
   (`725f2ff <https://github.com/Isra3l/MolSanitizer/commit/725f2ffe659213e45c1488fa95b0f24a4db20f08>`__)

.. _bug-fixes-4:

🐛 Bug Fixes
~~~~~~~~~~~

-  Fix an error that find_sulfonamide not function as expected -
   (`1818ea7 <https://github.com/Isra3l/MolSanitizer/commit/1818ea71c6b8856d0603f125c5860639d09886ab>`__)

.. _refactor-4:

🚜 Refactor
~~~~~~~~~~

-  Remove unused parameters (rmsd) -
   (`19bbd40 <https://github.com/Isra3l/MolSanitizer/commit/19bbd4067fdd2ba918d7534c9eabacef23e9d00d>`__)
-  Remove unused files in the repository -
   (`744f694 <https://github.com/Isra3l/MolSanitizer/commit/744f694c98720177145d3d3edeeefa29d729a7ae>`__)

.. _documentation-1:

📚 Documentation
~~~~~~~~~~~~~~~

-  Update README to match the method implemented in smi2db2 -
   (`36270e6 <https://github.com/Isra3l/MolSanitizer/commit/36270e61267e56bebb452c2231817d676cfead1a>`__)

◀️ Revert
~~~~~~~~~

-  Revert back to 300 initial conformations for better performance -
   (`31fabcb <https://github.com/Isra3l/MolSanitizer/commit/31fabcb4e8f238f691c27a2cd518e653e37fb85f>`__)

.. _section-4:

[0.1.0] - 2024-09-17
--------------------

.. _features-5:

🚀 Features
~~~~~~~~~~

-  Updated new rules and merged the SMARTS -
   (`217b61c <https://github.com/Isra3l/MolSanitizer/commit/217b61cd2d65fbe1f3e8589c1d5f7c52208b7dc2>`__)
-  Try to implement rotating hydrogen within stochastic sampling to
   increase diversity and speed up the mol2db2 process -
   (`4c6d05a <https://github.com/Isra3l/MolSanitizer/commit/4c6d05a3a5237f6cf85dbc7fcf66c1b4d454b42f>`__)
-  :zap: Boost the performance of stochastic sampling by switching
   between the two modes, based on the relationship between number of
   possible conformations and number of allowed conformations. -
   (`a4e7a57 <https://github.com/Isra3l/MolSanitizer/commit/a4e7a57dcb828759d54c4178f044c15b1151f91b>`__)
-  Added timing feature for mol2db2 workflow -
   (`e38916e <https://github.com/Isra3l/MolSanitizer/commit/e38916e5175263aa58123ff6703a4246baa73d3c>`__)
-  :sparkles: Small-ring Torlib updated! Msani should now produce up to
   10 (and favorable) rigid scaffolds based on the new SR-Torlib! -
   (`e33139e <https://github.com/Isra3l/MolSanitizer/commit/e33139e1f5223c8a84c037b7cf252a621588b132>`__)
-  Small-ring Torlib updated! Msani should now produce up to 10 (and
   favorable) rigid scaffolds based on the new SR-Torlib! -
   (`fcad867 <https://github.com/Isra3l/MolSanitizer/commit/fcad86777f0ef5bb3dc18c42d9723b88e96279e0>`__)
-  Now supports upto 8-membered ring as rigid part in smi2db2 part -
   (`de62a99 <https://github.com/Isra3l/MolSanitizer/commit/de62a9940b30ba6d0e0770aee225ba3271933e7d>`__)
-  Added the debug mode for testing on large scale -
   (`7b304e9 <https://github.com/Isra3l/MolSanitizer/commit/7b304e9bebf885c46f5f2158e75ae0df6947aaa3>`__)
-  Added an epsilon values so that angle scores at 0 can still have the
   possibility to sample -
   (`6afbc63 <https://github.com/Isra3l/MolSanitizer/commit/6afbc638f73949e1cff8a9c2cff36a37c51eba4c>`__)
-  First effort to embed multiple ring conformations and cover multiple
   regioisomers of sulfonamide-like structures -
   (`afd59b1 <https://github.com/Isra3l/MolSanitizer/commit/afd59b1294846c3346f77c0684d6a769a36075e1>`__)

.. _bug-fixes-5:

🐛 Bug Fixes
~~~~~~~~~~~

-  Removed meaningless rules, updated timing and catch an exception
   where no good conformations could be found (fused-ring systems) -
   (`d73bc8e <https://github.com/Isra3l/MolSanitizer/commit/d73bc8e3559175e3daa7130e53e54c6b80f7678e>`__)

.. _section-5:

[0.0.7] - 2024-09-01
--------------------

.. _features-6:

🚀 Features
~~~~~~~~~~

-  *(install)* Added toml file and fixed null arguments -
   (`61c1380 <https://github.com/Isra3l/MolSanitizer/commit/61c138077348b74af345a29aa34ef87613ce357f>`__)
-  :sparkles: Using srETKDGv3 (small-ring version) to hopefully reduce
   the failed cases with “boat” conformation of the rings with the
   previous ETKDGv3 (speciallized for macrocycles) -
   (`2970f10 <https://github.com/Isra3l/MolSanitizer/commit/2970f10515dbf69565183e75660606d27683be44>`__)
-  Msani_batch will now ask the user to confirm to remove the folder
   before removing it + skip the jobs with more than 1000 subjobs -
   (`9a6b76c <https://github.com/Isra3l/MolSanitizer/commit/9a6b76c9c52b4534a1dbfc8a168929b6915cbf86>`__)

.. _bug-fixes-6:

🐛 Bug Fixes
~~~~~~~~~~~

-  Fix a bug so that MolSanitizer batch mode still runs although the
   user asked for not to. -
   (`b518b03 <https://github.com/Isra3l/MolSanitizer/commit/b518b03479b7441ed41b1829e1c3a82849d57d11>`__)
-  :bug: Fix a typo in torsion scan that crash msani -
   (`4275824 <https://github.com/Isra3l/MolSanitizer/commit/4275824384d8567703a5234da77e015561a69e17>`__)

.. _performance-1:

⚡ Performance
~~~~~~~~~~~~~

-  :zap: Improved performance for the stochastic sampling, removed RMSD
   pruning dependent. -
   (`302e715 <https://github.com/Isra3l/MolSanitizer/commit/302e7158a72527bd08ebb2f5c9b8240579c38bd6>`__)

.. _section-6:

[0.0.6] - 2024-08-22
--------------------

.. _features-7:

🚀 Features
~~~~~~~~~~

-  Changing the default maxAttempts in stochastic sampling for more
   exhaustive sampling -
   (`aa88ccf <https://github.com/Isra3l/MolSanitizer/commit/aa88ccfec57bb4dbc8a75d54f317b71168847069>`__)
-  Failed stereoisomers-enumerated compounds should now print to the
   screen to notify the user -
   (`36846e1 <https://github.com/Isra3l/MolSanitizer/commit/36846e13334c7c290a6620aa16a0ec75f27602c0>`__)

.. _performance-2:

⚡ Performance
~~~~~~~~~~~~~

-  :zap: Efforts to speed up the conformers generator of super-flexible
   and symmetrical compounds -
   (`b6a04ad <https://github.com/Isra3l/MolSanitizer/commit/b6a04ad9adf4f988092b6c5af0eed96aede2deff>`__)

.. _styling-1:

🎨 Styling
~~~~~~~~~

-  Fix typos -
   (`e51eefc <https://github.com/Isra3l/MolSanitizer/commit/e51eefc47099fe49ccabe0598e260e4cc387de5d>`__)
-  :art: Improved logging of the time of running of each step of
   MolSanitizer (should now output hours:mins:secs) -
   (`a3ff715 <https://github.com/Isra3l/MolSanitizer/commit/a3ff715dc9ed4b16f84a690d0751e954c74e24a3>`__)

.. _section-7:

[0.0.5] - 2024-08-21
--------------------

.. _features-8:

🚀 Features
~~~~~~~~~~

-  Adopts the same technique of UCSF for rescaling the number of confs
   generated -
   (`01281aa <https://github.com/Isra3l/MolSanitizer/commit/01281aa690dcca0b0e56ac19e83fbd8c3557ed09>`__)

.. _bug-fixes-7:

🐛 Bug Fixes
~~~~~~~~~~~

-  :bug: Remove 5-membered ring as they are not working as expected.
   Added in CC bond as the last resort in case nothing else to align to.
   -
   (`1c9db8d <https://github.com/Isra3l/MolSanitizer/commit/1c9db8d5fd254125b218aa0e97e783476c0c014f>`__)

.. _section-8:

[0.0.4] - 2024-08-21
--------------------

.. _features-9:

🚀 Features
~~~~~~~~~~

-  *(smi2db2)* :sparkles: Rigid compounds without any rotatable bonds
   (or with only 1 conf during rotating rot bonds) will output all the
   3D conformations by Rdkit rather than only one like before. eg.
   steroids, morphine…🔥 -
   (`0ff023e <https://github.com/Isra3l/MolSanitizer/commit/0ff023ed4ee262100fc8baa67865dd9346b457a4>`__)

.. _styling-2:

🎨 Styling
~~~~~~~~~

-  :fire: Better logger for errorneous compounds -
   (`4627645 <https://github.com/Isra3l/MolSanitizer/commit/4627645bd555a5b9ae51476762cde4c070003c61>`__)

.. _section-9:

[0.0.3] - 2024-08-20
--------------------

.. _features-10:

🚀 Features
~~~~~~~~~~

-  *(Added the debug mode for strain_filter; The strained molecules now
   should be stored in another file.)* :zap: -
   (`921c6b9 <https://github.com/Isra3l/MolSanitizer/commit/921c6b98ff2cbd4bbc3e93e008f8fa60c47f11fe>`__)

.. _bug-fixes-8:

🐛 Bug Fixes
~~~~~~~~~~~

-  *(smi2db2)* :bug: Fix a bug so that rmsd only comparing between
   heavy_atoms –> boost the performance significantly -
   (`2ab67b2 <https://github.com/Isra3l/MolSanitizer/commit/2ab67b2d4bc3269186fa2d70e55d860822439ff1>`__)

.. _section-10:

[0.0.2] - 2024-08-19
--------------------

.. _features-11:

🚀 Features
~~~~~~~~~~

-  *(Strain_filter now has its own standalone script!)* :zap: The
   strain_filters now can be called by command ‘strain -i examples.mol2’
   -
   (`f05bf9b <https://github.com/Isra3l/MolSanitizer/commit/f05bf9b754f0ce49d239e2f258f4284147dcdd73>`__)
-  *(Strain_filter now has its own standalone script!)* :zap: The
   strain_filters now can be called by command ‘strain -i examples.mol2’
   -
   (`60a7958 <https://github.com/Isra3l/MolSanitizer/commit/60a795852eb6cea3283528b22d75dfb85f0e8b28>`__)

.. _bug-fixes-9:

🐛 Bug Fixes
~~~~~~~~~~~

-  *(Fix an error in strain_filter doesnt have main attribute ‘main’)*
   :bug: Reorganizing the main script to the main() function and
   redefine the scope of the Torlib variable -
   (`d91868f <https://github.com/Isra3l/MolSanitizer/commit/d91868f978de7fd777ff82fe008dec3506b871ba>`__)
-  *(Now MolSanitizer will try different conformations for desolvation
   with AMSOL.)* :sparkles: -
   (`e190e96 <https://github.com/Isra3l/MolSanitizer/commit/e190e9675a87f9a13161586510ea5d43c0286529>`__)

.. _documentation-2:

📚 Documentation
~~~~~~~~~~~~~~~

-  *(Better documentation for argparsers)* :memo: -
   (`844e4e3 <https://github.com/Isra3l/MolSanitizer/commit/844e4e3b43a65af150b92fa95f4b8116a1e3f0b6>`__)
-  *(Better documentations for argsparser)* - Added more details to the
   documentation of the argsparser -
   (`7d81d74 <https://github.com/Isra3l/MolSanitizer/commit/7d81d74df808404fd85a7a1862f57a4adfea4de2>`__)
-  *(Documentations for the new batch mode of MolSanitizer)* :fire: -
   (`abe3cfc <https://github.com/Isra3l/MolSanitizer/commit/abe3cfc707dfb5d7e4e48f299080cf37f6d8c347>`__)

.. _styling-3:

🎨 Styling
~~~~~~~~~

-  :construction: Fix Typos -
   (`e400636 <https://github.com/Isra3l/MolSanitizer/commit/e400636ea89e660f98c2af31c17c779f0176ce75>`__)

.. _section-11:

[0.0.1] - 2024-08-16
--------------------

Updated
~~~~~~~

-  Stochastic sampling with probs; second tolerance sampling for clash
   compounds; RMSD clustering for stochastic sampling. -
   (`8e63d2c <https://github.com/Isra3l/MolSanitizer/commit/8e63d2c3e98e268b6e3f3d4e32c0b7ae5cfa8b54>`__)

.. raw:: html

   <!-- generated by git-cliff -->
