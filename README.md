# RPGMaker_universal_modloader
A save file for rpgmaker vx ace(currently only vx ace) that allows whatever rpgmaker game you play it on to load content from outside of encrypted archives(or unencrypted).
No shenanigans, just drop the save file into whatever rpgmaker vx ace game you wish, drop the example Scripts.rvdata2 in, load save file 16, and you will have a main menu with a "new game" button that has been replaced with "test", not very impressive, but if you have your own version of rpgmaker vx ace, you can make scripts to overwrite scripts in already existing games, and distribute them without worrying about redistributing a creators work. 

TODO: 
ok maybe i was lying about the "whatever rpgmaker game", if the rpgmaker has script files that add additional fields to any of the 8 objects rpgmaker packs into a save file, it will crash. Fortunately, im going to upload a script that contains everything needed to build one of these save files, and once you save with that game, anyone can use that exact same save file to start the modloader.

WARNING:
dont download files from strangers.
While this shouldnt be against the TOS of Degica, im not a lawyer. In the making of this i did absolutely no reverse engineering of the encrypted archive, and since that is the only thing specifically mentioned as "not ok to reverse engineer" in the menual, i assumed save files, unencrypted data files, etc. Were completely alright to mess with. 
