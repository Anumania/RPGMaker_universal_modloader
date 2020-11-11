# RPGMaker_universal_modloader

## IF YOU WANT TO USE MODS:
download save16.rvdata2, download your mod of choice, place save16 in the same directory as the exe, place your mod into the mods folder, start the game, load save 16.
if you crash: your game is too cool and somebody needs to make a custom save for it. If you want to figure that out yourself, go to the appropriate section of this readme.

## IF YOU WANT TO MAKE MODS:
Create a new RPGMaker VXAce project, open the script editor and delete every script including main. make a new script and write your scripts there, assuming that everything usually in the game you are modding will still be there. Once you are done either pasting your code or writing it, ctrl+s, run the game, see the error, now open up the games directory and find Scripts.rvdata2. That is your mod. You are welcome to name it whatever you wish, preferrably not Scripts.rvdata2. 

## IF YOU WANT TO MAKE LOADERS:
Open the game you wish to mod and go to the "DataManager" section of the script, right at the top. Find `def self.make_save_contents`, and then put this code above it:
```ruby 
def self.make_route_code()
    route = RPG::MoveRoute.new()
    route.list[0].code = 45;
    modLoader = '
      @depth = 1
      File.open("Scripts.rvdata2", "rb") { |f|
      @scripts = Marshal.load(f)
      }
      @scripts.each_with_index do |script, i| 
        script[2] = Zlib::Inflate.inflate script[2]
        TOPLEVEL_BINDING.eval(script[2]) 
        end    
      #SceneManager.run 
      SceneManager.goto(Scene_Title)
    '
    route.list[0].parameters = [modLoader];
    $game_player.force_move_route(route)
  end 
```
Then, on the first line of `self.make_save_contents`, add `make_route_code()`.
Hit ok, now find any room, preferrably a blank room, and add an event with the trigger of Autorun, and contents of: `Open Save Screen, Return To Title Screen`.
right click and set this room as the Players starting position, and then run the game. Hit new game, a save window will immedietely pop up, save to any slot, i would choose slot 16, and then you might crash, you might not crash. Either way, find the save16.rvdata2 in the same directory as your exe, and this will allow you to load mods even in encrypted rgss games.
