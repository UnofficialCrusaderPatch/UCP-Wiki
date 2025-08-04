> [!NOTE]
> Work in progress! \
> TODO:
> - ~~Add more stuff (none of the sections is fully complete yet, some are plain-empty so far)~~ 
> - Using this list of ideas to make something that remotely resembles a roadmap, or at least some more structure / metadata 
>   - Going the contents again, re-sorting some of it and adjusting the categories a bit / introducing some sub-categories that help summarize groups of similar, smaller points more easily. (If you think there's some useful category names that are not currently in there, please feel free to point it out.)
>   - Probably also something in the ways of prioritization/relevance/size would probably help, albeit ofc everyone working on the UCP is free to work on things they personally deem relevant or enjoyable.
>   - Extracting some sort of summary for a higher-level overview of areas, which would be a bit closer to the initial post this originated from
> - Encapsulate a few more things into their own issue threads to link to 


## Potential areas of focus
- [Potential areas of focus](#potential-areas-of-focus)
- [Game UI/UX](#game-uiux)
- [Game Visuals](#game-visuals)
- [UCP Customization and UI/UX](#ucp-customization-and-uiux)
- [User-Generated Content](#user-generated-content)
- [General Gameplay Improvements](#general-gameplay-improvements)
- [AI Improvements](#ai-improvements)
- [Map Editor Improvements](#map-editor-improvements)
- [Multiplayer Improvements](#multiplayer-improvements)
- [AIV-Editor Improvements](#aiv-editor-improvements)
- [Communication and Guidance](#communication-and-guidance)


## Game UI/UX
Consider small UI/UX improvements that provide improved QoL or (easier) access to previously inaccessible features. E.g. additional/improved ingame UI, graphics API replacer improvements, or similar. Besides, especially for input handling / controls, there's some long-desired improvements waiting to be implemented. \
Some examples: 
- [Show load button in skirmish lobby](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/42), 
- [Display ingame indicator for reaching the unit limit](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/50), 
- Make castle builder, historical campaigns and play scenario menus accessible in extreme
- Increase size of unit dots on minimap (exists already as rebalancing entry for the old rebalancer)
- Minimap that displays the entire map
- Fix semi-broken rally points for cathedral monks (ignored by all newly-recruited monks as soon as the first monk arrives there) 
- Fix invisible map descriptions in skirmish / mp lobby screen 
- Provide some "shortcut" from the granary's food types menu to trading food (in the form of some button leading there directly). It always felt weirdly asymmetrical compared to armoury/stockpile that the granary is not at all linked to trading the goods stored in it. 
- Additional hotkeys for the game (e.g. selecting different building types or other objects for placement, and/or opening different menus, as is common in many other RTS games). 
- Input remapping system / customizable hotkeys \
  (Note: This and the hotkeys can also be implemented very incrementally, extending the systems over time. If it initially only covers a few things, or is only configurable via some JSON text file, that's perfectly fine - it still provides significant added value and can generate feedback that helps guide further improvements.) 
- Fix sounds being played only from part of the game window (I think limited to pre-HD-update resolutions, i.e. 1024x768?) 
- Fix sounds from videos (e.g. some vanilla AI messages, some workshop videos) disregarding the game's sound volume game settings
- Fix FX sound volume setting being initialized to wrong value when starting the game (ignoring the fx sound settings value) 
- SHC-E: Restore visibility of hidden menus (create scenario maps, play custom scenario, play castle builder). Those menus can already be accessed ingame via some tricks and workarounds, and are then fully functional (same goes for the content that can be accessed that way), so it is just nonsensical to not have them displayed regularly. 


## Game Visuals
Do not waste time on hugely complex visual changes like generally higher texture resolution / pixel density, higher animation framerate or similar. (The effort to rewrite the game's rendering pipeline and create all-new higher-res textures and animations, while also maintaining stability and compatibility with existing texture packs... is just not really feasible, nor worth it.) \
However, small-scale changes within the existing system's limitations can provide value with reasonable effort. 
- Allow changing texture packs at runtime
- Enable using multiple texture packs simultaneously (one per player), even if only a few things for the beginning, like some buildings and the Lord. 
- Add overlays for more buildings that do not have an overlay in vanilla (e.g. some of the towers, gatehouses) similar to those for the tower1 (watchtower) in vanilla. (Note: Reconquista also kinda requires this.)
- Make the max height for a select few key textures (wall and cliff sides) configurable, because with vanilla they loop for tall walls/cliffs, which looks kinda stupid and heavily limits options for retexturing them nicely. (Working prototype for this exists, iirc) 
- There are 2 "growth stages" for dead trees. Currently, both stages show the same texture, but the sprite sheets for trees actually contain 2 different sprites. 
- Add a (customizable) multiplier for the despawn time of all dead unit corpses. Allows players to have corpses remain longer (immersion / more dramatic battlefields), or let them despawn faster. 
- Fix skulls spawning ever-more ravens 
- Fix AI flags/braziers getting placed many times in the same spot 
- Adjust the tower entrance door overlay texture's height offset depending on whether a low or a high wall is adjacent to the tower (currently, even low walls display the entrance door at the same height, thus floating in the air, looking ridiculous). 


## UCP Customization and UI/UX
We want to make sure there is no confusion for users in the GUI, and players can effortlessly navigate and use it to customize their game. 
- Improve content search (tagging of extensions, searching by tag and free text search)
- Show dependencies between extensions (reverse dependency search)
- Improve error handling / messages! E.g. _„FATAL Failed to run main.lua (...) [callstack]“_ is NOT understandable to normal users, and does not point them to potential causes or solutions for the issue. Something like _„outdated game version is not supported, please update!“_ or _„your language version of the game seems unusual; the following feature is not supported there: [name of some specific feature / setting]“_ would be a lot more helpful. \
  Note: _We_ might be able to utilize stacktrace info, but it creates a better atmosphere when out of 10 people trying with v1.3, 9 get sufficiently informed how to get v1.4 by the UCP GUI and only 1 guy posts „can’t launch game with UCP!“ on discord or github and needs manual half an hour of manual attention from us, including sending us his log file that contains the stacktrace anyway. Currently it feels rather the other way around where 9/10 do talk to us about how UCP doesn’t work for them. Maybe stacktraces can be put into a log file, or displayed/copied via some button in the error popup, but it shouldn't be the first thing the user encounters. 
- Improve on UCP stability, primarily by testing and double-checking new versions work properly before releasing them publicly. With UCP2, the last couple updates were possibly a bit too large and took "forever" to release, but things mostly just worked, without people encountering and reporting bugs and issues all the time. (Yes, UCP3 is technically still "in alpha", but it doesn't necessarily feel that way.)
- Add periodic or manual update checks without requiring the user to manually restarting the GUI. 
- Translations! UCP2 was available in multiple languages, but UCP3 is not (yet). 
- The „UCP2 Legacy“ extension has been named like this because of plans to modularize and cleanup the features in there and put them into different extensions afterwards. However, until that happens (if it happens?), we might want to think about whether the naming for this plugin is ideal, or what we can do to make it more intuitive for people to use this. Maybe some guidance can solve this, though (see below). 
- Make some UCP-settings customizable at SHC runtime, perhaps? 
- Currently, much of the UI is focused on content usage, but not content creation. We need more QoL/UX improvements for content creators! 
  - Option to create empty templates for new plugins (e.g. "AI pack" or "map pack" or "rebalance") that generate the required folder structure and config files, so people do not have to manually remember and create all of that from scratch every time. 
  - Button to open the extensions folder (in the windows explorer / linux equivalent)
  - Button to show/select a particular extension inside its containing folder


## User-Generated Content
Generally, we want to encourage and assist people with adding new, high quality content to the UCP store, as well as improving managing and finding the content you are interested in more easily as the store fills more. But if we can, we should also aid people in creating new content in the first place. 
- See [Map Editor Improvements](#map-editor-improvements) for some improvements for creating new maps. 
- Allow custom skirmish trails for regular Crusader as well, and make such custom trail definitions available as extensions via UCP store (for SHC and SHC-E respectively). 
- Remove the x3 Gold multiplier for extreme Trail (optional addition: allow custom start goods for individual skirmish trail missions)
- Maybe even add support for custom campaigns? (See [Custom Campaigns](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/51) for more details.) \
Ideally have could even set up a more flexible campaign format that allows using skirmish-trail-config missions together with regular scenario missions and skirmish-scenario maps in a single campaign. (At the end of the day, a campaign only needs to care about a list of missions with a defined order of playing/unlocking, and the individual missions can do "whatever they want". That way, we can freely combine the best from skirmish trails and the historical campaigns section.) 
- Enable scenario events for skirmish-type maps (would enable scenarios involving both AI and events, as well as co-op missions for MP with objectives other than „kill all other players“)
- Have an option to disable spawners on all maps (allows playing any SHC-E maps with spawners, without having to deal with those spawners' disruptive gameplay). 
- Provide some improved handling for the cr.tex file and changes to it. Currently, it is pretty much impossible to merge different changes to parts of the file, while touching parts of the file is required for many different changes. Notably, with the new UCP3 AI format, changes for AI descriptions / message texts can already be specified separately now, which makes it a lot easier and more modular to do such changes. 
- Allow hiding Maps from Map selection for custom skirmishes or the "play custom scenario" menu (campaign-only / skirmish-trail-only maps not fit for general standalone playing only clutter the map lists otherwise)
- Continue to work with content creators to release some awesome existing community content as UCP store entries. Maps/mission packs, AIs, texture packs (e.g. Monsterfish's adjusted SH1 and SHC texture packs, or also Steinhauer's nordic pack or Salen's "volcanic" pack), etc. 
<details><summary>Example: Salen's pack, quite the change from vanilla visuals :D (**show image**)</summary>

![Salen's Pack Teaser](https://github.com/user-attachments/assets/85df3e40-77c4-4681-b6cc-7168121b8515)

</details>


## General Gameplay Improvements
Improving gameplay, possibly even providing new features, game modes or supporting alternative playing styles is always a plus, if we have good ideas with feasible scope/complexity. 
- Polish, expand and use the rebalancing module (standardized system for many simple small-scale changes / value adjustments)
- Choose building default entrances based on keep orientation (instead of being identical for all players) - which would solve issues with siege tents (for AI and human players) as well as unintuitive player eco asymmetries. 
- New features (like the healers healing units) can provide novelty and help improve overall gameplay. \
  Some example ideas:  
  - Make hunters shoot enemy units (as they already do outside skirmish), 
  - Reworking religion / priests beyond a simple rebalancing value change (see [Priest Behaviour Rework](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/48)
  - Disable "stance inheritance" (when selecting a number of units, they all switch to the stance that the majority of the selected units had before), since this messes things up more often than not
  - Vary ranged units' targetting priorities based on their unit stances (allows for more strategic depth and control over unit behaviour as a player)
  - Assassin visibility has 3 states: Invisible, Partially Visible (semi-transparent) and Fully Visible. Currently, enemy ranged units already target Partially Visible assassins. It would be better though, if they would only target Fully Visible assassins. That way, the detection range difference between partial and full visibility could also be tweaked to provide more nuanced balancing for assassins, as they are a very controversial unit.  
  - Rework stables' horse spawning: Reduce their basic horse spawn rate, but allow them to "refill" their 4 horse spots without requiring the recruited knights to die first. That way, it becomes more feasible for AIs to use knights without requiring huge AIVs filled with tons of stables. It also potentially improves knight balancing for multiplayer.  
  - (Experimental idea: Display enemy assassins as workers of the viewing player (e.g. hunters or woodcutters) while undetected, instead of making them invisible. That way, the player doesn't immediately know this is an enemy unit, but depending on location and movement patterns can already *suspect* it, and knows that there is a unit there at all. This would be a visual change only, i.e. assassin unit stats would be unaffected; while climbing walls, an assassin would be temporarily "uncloaked" visually (as workers lack a climbing animation, and as such an action would be very suspicious either way).)
- Make it possible to use map settings like trading, building, weapon production and recruiting restrictions for skirmish maps (trails and custom skirmish), as well as multiplayer as well. 
- Make it possible to set recruiting restrictions for cathedrals and the engineers guild at all.
- Update attack behavior for spawner Units - right now they behave like vanilla attack army (probably main army slots?), and are not benefitting from UCP attack behaviour improvements
- Potentially do improvements to the "fluidity" of gameplay, if possible (like pathfinding updates or how often AI can trade per game month, maybe even reducing the lagspikes happening when larger amounts of units are given movement orders). 
- Finish the replay system! (arguably, this is useful both for multiplayer as well as regular singleplayer, AI battles and game balancing testing or mechanics analysis videos) 
- Make it possible to specify an AIV number for each (AI) player that should be used in a custom skirmish match (basically replicating what skirmish trail missions already do), via a new toggle button in the skirmish lobby's player list (default being "?" (random), and clicking cycles through numbers 1-8 then back to "?"). That way, players have more ways to customize their skirmish experience - be it for testing a particular new AI, AIV or map, for reliably replicating a prior match's setup, setting up their own specific challenges, or exploring some of the less-frequently chosen AIVs for a particular AI character. 
- "Officially" add the "active spectator mode" (both a human player and an AI being present on player 1 slot at the same time) as an option. Currently, it can already be enabled via some tricks/workarounds, but that's always a bit hacky and can potentially "corrupt" maps unintentionally. 
- Make spectator mode configurable in the skirmish lobby (some button for player 1 to toggle between `active spectator (human + AI) | passive spectator (AI only) | off (human only)`
- Potentially, we can even take this a step further: If we add an option to specify the AIV number to use for player 1 spot's AI for custom skirmish - either via aforementioned ingame UI in the skirmish lobby screen for every player, or as an UCP3 GUI setting in the context of spectator mode - and add an option to switch off parts of the AI behaviour for player 1 (e.g. military unit handling/recruiting, trading, placement of AIC-defined resource buildings outside the castle), then we basically have a working system that lets players create "castle presets" (AIVs), lets them choose one of them, and also semi-automatically sets up those castle presets in the game (AI following AIV build steps). That way, players have a cool new feature that allows them to build and maintain fanciful own castles in skirmish, and they can also get more familiar with the creation of AIVs in general. 
- Fix hunter pathfinding issues (no targetting of deer that is too close to them)
- Fix/improve deer breeding (in vanilla SHC, it is always just a matter of time until they go extinct (unlike for SH1), as their breeding is dysfunctional)
- More worker pathing improvements (e.g. https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/48)
- Unit formation / movement commands (e.g. „spread out!“, dense formation (like on walltop), loose formation, line formation)
- Hotkey to reduce current unit selection to only injured units (below 50% HP, potentially the percentage being configurable; kudos for the idea go to _Settlers IV_). That way, you can more easily pick injured units to send them away for healing them back up near a healer. 
- Improve unit pathing around fire: If there is a path around the fire, take it instead of running right into the fire. 
- Slow down / limit instant fire spreading through adjacent buildings
- Disable getting back resources from deleting burning buildings. 
- Fix that selecting a unit temporarily slows down running units (e.g. knights) to walking
- Improve handling of units with different movement speeds: Make them not slow down on selection and default to running at their individual speeds; double-click for moving at the same speed. (Vanilla: Slows down when selecting, default to same speed, double-click for moving at individual speeds.)
- Revisit the old WIP extension that allows placing buildings over of workers. Ideally, we can make it smarter (displace instead of despawning units, or limit despawning to blocked tiles only – open farmland or other walkable areas inside a building's area shouldn’t despawn units on them!), and ofc multiplayer-compatible. Ideally, it would also be somewhat configurable. One interesting option might also be limiting the feature to „ambient units“, i.e. neither military nor working population, but only mothers and children, jester, travelling fair units, drunkards, hunting dogs, ghosts, as well as possibly unemployed peasants - effectively treating them all like chicken, who are another ambient unit that can already be built-over. 
- Adjust aggressive and defensive stance provoking and building targetting ranges to have more relevant use cases; potentially also tweak how they work in general, to improve their usefulness. 
- Make dead units no longer count for taking over (or preventing a takeover) of gatehouses. There's a number of reasons to implement this change: It just doesn't make any sense that a corpse still defends or conquers a structure against (alive) enemy units, and does feel both unintuitive, random/unpredictable (as different unit types have vastly different "death animation" as well as "corpse despawn timer" lengths), and also frustrating. Last but not least, it also happens to make assassins (quite short despawn timer) particularly bad at their original core role in the game - climbing walls and conquering badly-guarded enemy gatehouses (a game mechanic that is already quite underused by most human and AI players). 
- Fix projectile trajectories when aiming at units that are currently slowed down (by swamps, fords, uphill). Currently, all ranged units constantly misfire while targetting slowed-down units, due to ignoring the slowdown and shooting too far ahead of the unit. (Terrain that slows down approaching troops should be a hindrance for assaults, not a nonsensical invincibility cheat code that also works quite inconsistently for different unit types.) 
- Add an option to prevent spawning of „ambience units“ (hovel mothers/children, jesters, drunkards, ghosts, chicken). Especially when playing on non-Extreme, this should save a fair bit in terms of global unit limit usage, which comes very handy in matches with many AIs. At the same time, this would also enable players to not have to deal with those "useless" and semi-randomly wandering units blocking construction spaces in competitive gameplay without requiring more invasive options such as allowing general placement of buildings over own units. 
- Fix units disappearing from control groups if reselecting them with the control group number key while they move onto a gatehouse
- Fix keep entrance becoming temporarily blocked (pathfinding bug)
- Fix that weapon type restriction settings for weapon production buildings are generally ignored for scenario maps
- Fix/rework FireBallista targetting to not all lock onto a single target, and instead behave more like all other ranged units, who spread their shots over multiple enemy units. (Currently, whenever you have a group of more than maybe 2-3 FBals, they end up losing most of their damage to massive overkill every time they shoot, often making it almost useless to even have more of them. 
- Automarket with proper balancing (i.e. using it comes with some sort of cost, trading tax %, potentially employ a worker there)
- Add hotkeys (e.g. shift / ctrl) for batch-recruiting and batch-buying/selling
- Allow setting to sleep individual buildings as an alternative to setting to sleep all buildings of the same type. 
- SH1 had 4 difficulty tiers that could be selected for scenario missions. SHC does not offer this functionality to the user via the vanilla GUI, but probably the code still contains most or all the relevant game logic from SH1 to make it accessible. 
- SH1 had score end-screens for scenario missions. This provided players a way to compare their performance to previous own runs, or with other players. Besdies, it is also just a very general "game-y" thing to have a highscore for missions. If the internal logic for it is still present in SHC, it could be cool to make this available again. 
- Make treb/cat accuracy balanceable (currently it is like a boolean that uses rather large random spread radius when on, and 100% pinpoint accuracy when off, but the spread radius itself needs adjustment... Altaruss know more details)
- Allow running SHC and SHC-E in parallel (for testing and development of content and features)
- Maybe we can achieve some sort of cooperation with the [SHCPlayer mod](https://www.moddb.com/mods/shcplayer) by JuGGerNaunT? By now, it has been updated to work with v1.41, and there's a bunch of cool improvements there, including: 
<details><summary>SHCPlayer contents (excerpt): (**show list**)</summary>

- custom ingame UI for some settings adjustments and new features
- fixed detection of invisible units and structures: you can no longer detect invisible enemy units and structures with the preview of a building
- fixed double workers: you can no longer use sleep trick to assign more that one worker to the production
- fixed stone teleport: blocking path to stone quarry no longer teleports stone to ox tether
- fixed fire watchers stay at 0 popularity: fire watchers no longer stay with you at 0 popularity
- fixed apple orchard size: apple orchard size after its construction has been changed from 11x11 to 12x12. it correspond to the size of its preview
- fixed moat restoring under draw bridge: closing of the draw bridge no longer restores moat under it
- fixed tunneler selection using bind keys: you can no longer select tunneler with bind keys after you send him to dig tunnel
- added King of the Hill game mode. /koth lobby command
- added observer mode. /observer or /obs lobby command
- option to toggle window mode
- option to change player color and /color lobby command
- option to change network latency
- save lobby settings in config file
- improved moat planning in multiplayer matches
- adapted avatar transfer to fit modern network bandwidth
- adapted map transfer to fit modern network bandwidth
- framerate independent camera movement
- fixed v1.41 send map button
- fixed destruction of siege engines. now engineers are destroyed together with siege
- fixed unit binding in multyplayer. now bind group is available immediately
- fixed bug that lead to cow carcass disappearing when it hit nearby area of siege unit
- fixed incorrect destination point for military units
- fixed route stuck for all labour units
- fixed fast workers bug
- fixed building's destruction gives double resources bug
- fixed rally point sprite for horse archer
- fixed attack focus of quarry stone pile
- fixed missing space warning for destroyed buildings
- fixed draw bridge destruction when neighbor building is destroyed
- fixed cathedral rally point
- fixed situation when labour and siege units stuck in a moat
- fixed destruction of units hidden inside building
- fixed bug that lead to climbing on a ladder back and forth
- fixed assassin attack during climbing
- fixed plants visualization for some maps
- fixed stockpile destruction
- fixed color table for some units
- fixed save file name in multiplayer matches
- deselect preview of the unique buildings after placement
- tent and tunnel deselection disabling has been improved
- draw preview of the building during camera movement
- show version mismatch message in lobby chat
- changed order of armory, stockpile and market products so they match each other
- tons of other less significant bug fixes
- Shift + drag to draw moat line (similar to building a wall)
</details>


## AI Improvements
- Work towards fixing long-standing AI issues (especially related to AI attacks and raids). 
- [Implement an actual "Any" target choice](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/52)
- [Improve AttMaxDefault AIC Parameter](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/49)
- Fix AIV unit spots being offset to one side based on the player's keep rotation
- Add an AIC parameter for max siege engines per attack, iterate the list of 8 siege engines in a similar fashion as the lists of farms or def units (i.e. multiple times if the max is set to values larger than 8). 
- Allow monks and tunnelers as sortie units, tunnelers as raid units, and rams as harassment siege engines (or raid units, if that happens to be easier to implement) in AICs. Also allow "None" as sortie unit (which currently leads to the AI malfunctioning). 
- Cancel pitch ditch lighting orders for AI-controlled European archers after one shot. (Vanilla SH1: They shoot once, then stop. Vanilla SHC: They don't shoot at all. Current UCP state: They shoot endlessly if the target pitch ditch tile is obstructed. Desirable behaviour: They shoot once, then stop.) 
- Do not allow AI to order their archers to light pitch ditches from other players with fire arrows. (Currently, they will happily lit allied or even enemy pitch ditches, with often catastrophic consequences such as setting on fire allied castles. Also, human players cannot light enemy pitch ditchs that way (nor see them), so AI shouldn't do it either.) 
- Turn the threshold for "enemy unit power" near a pitch ditch that is required to trigger the AI ordering the pitch ditch to be lit into an AIC variable. Currently, it is a global constant shared by all AIs and by default set to zero, which makes all AIs behave the same in this regard, while also being way too trigger happy most of the time. 
- Make AIs actually use melee unit troop spots in their AIVs properly. Currently, those for swordsmen, pikemen and Arab swordsmen are ignored, and those for slaves sometimes even get filled with ranged units. Ideally, also _add_ the ability to place troop spots for monks and tunnelers to the AIV editor, as those are missing entirely in the vanilla AIV editor UI. 
- Make the behaviour for melee def units (patrolling between available spots / standing in place) an AIC parameter instead of a globally hardcoded constant depending on unit type. (In vanilla, macemen and spearmen patrol; so do horse archars. Assassins and knights don't... and all others just ignore the spots and stack on the keep instead.)
- [Improve and AIC-ify AI panic gold tributes](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/47)
- Allow AI-to-AI resource and help requests: Requests by allied AI players should be treated exactly the same way as requests by allied human players, instead of being skipped. 
- Add AIC parameters for the sortie recruitment probability. In vanilla, sorties are always recruited and prioritized over anything else, which often drains a lot of valuable gold and/or weapons from the AIs for little effect, and also generally heavily limits AI modders' ability to develop differently-behaving AI characters. (As a hacky "workaround" for the complete lack of control over sortie recruitment, many currently use a trick to disable sorties for their AIs entirely by setting Monks as sorties, since those are generally ignored by the AI for whatever reason.) 
- Add an AIC parameter for toggling between the current DefUnit recruitment behaviour ("try to recruit equally between all DefUnit entries, skip if insufficient goods, independent of current distribution of existing units") and a new variant ("try to maintain equal distribution, i.e. reserve equal unit count for each DefUnit entry, and do not 'replace' one type of unit with another"). That alternative behaviour makes it easier to balance more diverse unit compositions that are currently avoided by AI creators due to the lack of long-term unit distribution control. 
- Have separate unit slots in the AIC for outer patrol def units (as opposed to wall def units). This allows more diverse AI behaviour, and also allows more control to achieve senseful usage of the outer patrols. (E.g. horse archers, knights or pikemen may be useful in outer patrols, but they are rarely useful as a wall def. Meanwhile, slingers or archers as outer patrols make less sense than on top of walls and towers, as they tend to die very easily outside.) 
- Fix siege tent placement (so far, siege tents are sometimes placed way too far away, or too close to enemy walls, or just not at all; often times they are also placed back-to-back without any gaps, leading to obstructed entrances for some tents)
- Fix engineer bugs (details needed, may have existing UCP2 github issues; but basically the AI doesn't handle them correctly in some cases, leading to wrong unit counts and other issues)
- Fix AI despawning their own attack units when no pathing to own keep is found
- Fix AI attack army units sometimes freezing in place indefinitely when all laddermen die
- Fix AI attack and harassment siege engine behaviour: Sometimes, FBals/Cats roll into enemy melee range without attacking. 
- Fix AI often no longer building harassment siege engines at all later in a match. 
- Fix AI overbuilding existing harassment or def siege engines with new harassment siege engine tents (which may also contribute to the previous issue?). 
- Improve raid behaviour: instead of targetting the oldest (accessible) buildings of an enemy, allow targetting nearby (acccessible) enemy buildings, to avoid endless, nonsensical suicide raid maneuvers
- Fix harassment siege engines getting stuck inside/behind their own castles
- Attacking assassin pathing improvements: a) assassin slot: do not go for gatehouses of other players than the attack target (and ideally: not for gatehouses with drawbridges, if others without a drawbridge exist), b) other slots: act as if castle is open, even when it is not - when the castle is open somewhere, they climb across walls to reach the keep, which is a lot more useful than them mindlessly attacking walls with their blades. 
- Rework and AIC-ify attack increase factor.  
  - This allows different dynamics for different AI characters, e.g. some starting out with a smaller first attack but scaling up faster, others starting out with a larger base army but scaling up more slowly (for more frequent attacks).  
  - In vanilla, the (global) increase factor depended on the starting conditions (Normal/Crusader/Deathmatch and/or Human/AI advantage). Maybe such a distinction based on match starting conditions or a global, or via a UCP-GUI-configurable global multiplier similar to the current implementation, could be integrated with the new AIC parameter, so that players can still have a global modifier to customize their overall playing experience, while individual AIs can still scale individually. 
- Add an AIC-parameter or two for customizing well-sleeping behaviour. That way, AI creators can have more control over the vanilla behaviour of setting all wells and water pots to sleep when low on gold. Parameters would define a threshold for "low on gold", as well as a duration value specifying for how long the AI needs to be below the "low on gold" threshold value before wells should be set to sleep. (Note: Different AIs already seem to differ in that regard in vanilla by some means... ~~so possibly one of the current Unknown's is secretly already related to this?~~ it seems to be some more complex behaviour not tied to a single AIC parameter; all European-only vanilla AIs (except Abbot with monks) don't normally set their wells to sleep, while all Arabian ones set their wells to sleep below 500 gold... but a Snake with removed mercenary units/laddermen still does that, too). 
- Add an AIC parameter for minimum wood. 
- Fix that the AI is trying to path through (non-conquered) enemy gatehouses. (Currently, troops think they can march right through enemy gatehouses, thus often move their melee troops there, then the gate closes, troops repath, often finding another gate, marching all the way over there, etc... instead of actually attacking any enemy structures, unless they manage to surround the enemy castle to keep all gates closed.) 
- Fix the AI stacking WallDecoration objects on the same spot repeatedly, leading to many excess, stacked sprites and visual errors. 


## Map Editor Improvements
We want players to be able to create high-quality maps and scenarios with as little avoidable hassle and pain as possible. Many of the community's most experienced mapmakers also regularly use various external tools in recent years, but integrating them with the UCP in some way or another could make them more available, improve their usability and potentially offer new ways to enhance and expand them. 
- Integrate existing map creation projects (mirror tool, upcoming random maps generator by Altaruss, upcoming "image-to-map" tool by gynt, template/utility maps, map testing AIs, etc.) with the UCP as extensions
- There's some CE scripts that extend the map editor's functionality with many little helpful things. However, as the list of those things gets longer and longer, it becomes more difficult to keep a good overview. Also, knowing feasible/usable value ranges for many parameters is not trivial, so some "sanitation of user input" issues can arise when used directly by less "expert" users.  
  - Providing (read-only) info (e.g. number of units, buildings, rocks and vegetation, number of groups and different animal types, etc.), which could probably be displayed ingame as some toggleable info text overlay with relatively little effort.  
  - Making previously inaccessible objects accessible for placement (e.g. all growth stages for trees, SH1 shrubs, SH1 gravel terrain, apple trees, siege tents, some additional building types, signposts for skirmish maps, ...).  
  - Hotkeys and other UX improvements (e.g. providing hotkeys to select and switch between frequently-used objects, submenus and brush sizes, updating the menu even when not currently hovering over it, updating up-to-date random rock rotation preview).
  - Customizing map editor placement tools by changing hardcoded parameters (e.g. spawn counts for animal herds, controlling rock variants, extending min/max height limits for smoothing and other height-change tools, setting (and displaying) plateau tool heights on the fly, customizing wall height values, river depths, etc.).  
  - Customizing map properties (size, player colors, etc.).  
  - Adding and editing events and conditions, including ones that are unavailable in the scenario editor UI (e.g. time on/off, binks on/off, cede castle) or have inadequate limitations for their parameters that limit their configurability in the vanilla editor (e.g. invasion troop numbers are 32bit integers, but are limited in the UI to only 10 for some unit types, and 50, 100 or 200 for others; invasion player is limited by the UI to player2/3, but could be any player in theory, including player1; resource amounts for starting goodas and event conditions, as well as repeat intervals for invasions skip certain random values).  
  - Directly setting game speed to very low or high values for testing purposes.  
  - ...
- Fix hidden/broken functionality for switching between different map types (king of the hill for multiplayer, as well as generally selecting different types for singleplayer maps). Nonsensical decision to disable pre-existing UI buttons from SH1 which leads to many issues for SHC mapmaking, while the internal functionality still exists in the game. 
- Make SHC-E maps generally compatible with SHC (or provide a way to convert them back to an SHC-compatible format somehow). 
- Make it possible to import/export standardized map properties (map type, size, starting goods/gold/date, trading/unit/building availability, description text, start tax levels/rations/gold (yes, again, separate value!)), as well as the list of scenario events for a map, via the UCP (e.g. in json or yaml format). This would allow editing them via any text editor, reusing some event presets, but also make usage and testing of vanilla-hidden event types and conditions a lot easier without requiring complicated ingame UI reworks. \
Last but not least, this would also enable the UCP GUI to potentially display some relevant map properties (like map size and type) for e.g. map packs in the UCP store in the future. 
- SHC removed an entire class of events that SH1 had, which is messages. Considering pretty much everything else was untouched compared to SH1, it might be possible to re-enable message events. If that is doable, this would also make it a lot easier to include custom messages for user-created scenario maps. 
- Make it possible to erase seagulls


## Multiplayer Improvements
We want to make multiplayer accessible, enjoyable and configurable so that different people can play to their liking. 
- QoL improvements, e.g. 
  - Allow players to change colors (maybe via lobby chat commands?)
  - Improved ingame and/or game-end statistics 
  - Better chat (history) display 
  - Replay system integration 
  - Improved autosave system (cycle between several autosave slots instead of always overwriting the same slot with the very next autosave; or add player names or date/time to autosave; possibly archive old autosaves in a subfolder; allow shorter autosave intervals than 5mins for less loss of progress when loading) 
  - Ability for the host to change game speed in MP at runtime 
  - Additional MP lobby options/UI improvements, etc. 
  - Fix issues with player names and chat messages sometimes turning invisible (seemingly random), both in MP lobbies and ingame
  - Display warning in lobby if a player has a different UCP config than the host
  - Enable syncing host’s UCP config with all lobby participants (Note: Some specific things, like AI names and messages may be tricky to sync correctly, if players with different game languages play together!)
- Multiplayer stability improvements (networking code improvements or parameter customization to avoid issues where possible, e.g. input latency („fake lag“) parameter. Ideally, some parameters could also be adjusted during the game by the host (e.g. via new GUI elements or text-based chat commands), or at least in the multiplayer lobby screen --> ties in with QoL improvements for MP lobby options/UI) 
<details><summary>Example: Settlers United ("the UCP for _Settlers IV_") provides custom options UI in multiplayer lobbies; some of the option can be used/changed during a running game as well. (**show image**)</summary>

![Settlers United Multiplayer Lobby Options](https://github.com/user-attachments/assets/66541431-c6d5-49e9-b564-6937e65e9535)

</details>
- Integrate and polish Showdown's steamworks connection system (RedirectPlay) for MP (small drawback: Steam-exclusivity) to make it more accessible to find a lobby directly ingame
  - Ensure stable functionality: Host migration, preventing late-joining (joining running matches), leaving/joining players in-between matches, private/friends-only lobby options functionality. 
  - Improve UX: Improve lobby creation / pw enter UI, consider adding more info to the lobby search UI (e.g. indicator for running games, player count in lobby, settings/gamemode used by lobby)
- Enable dynamic alliances in MP (in SH1, this setting actually exists as a MP lobby option!)
- Potentially we can make it work to have ranked games, and a ranking system with some ranking tables to be viewed over the UCP website? (see "Settlers United" for a _Settlers IV_ community modding project, similar to the UCP, that did just that!) 
- SH1 had a "king of the hill" multiplayer gamemode. Probably there's disabled remnants of this still in SHC that could be used to enable this for SHC multiplayer as well. (The SHCPlayer mod does this already)
- Also, more generally speaking, if possible, some additional gamemodes could be quite interesting. E.g. 
  - "2 Player Co-op": 2 (human) players sharing the same "logical" player slot so they can share and control the same eco, units, etc. (a bit like the so-called "active spectator mode" in singleplayer that allows sharing the same player slot with an AI, something that is possible and used already)
  - "Multiplayer scenarios": Maps with scripted events, invasions (and possibly also AI opponents) that can be played by multiple players. 
  - Perhaps allow starting any singleplayer map in MP via "2 Player Co-op" (i.e. multiple humans interacting all with logical player 1) --> Instantly we get a cooperative "freebuild", cooperative campaigns, cooperative scenarios
- Make MP-relevant info more available in the UCP3 GUI regarding what to do consider / how to play MP with the UCP, promoting relevant discords, setups, helpful info, etc. Maybe even displaying currently open MP game lobbies? 
- Improve moat-drawing in MP


## AIV-Editor Improvements
One of the longest-available types of user-generated content, and for a while potentially the most active field of community interaction and innovation, is AIVs. The AIV editor has been available for over 20 years now, and has never really received much love. (Notable exceptions were some user-made visual reskins, and a small tweak that came with UCP v2.06, allowing placement of more than 5 troop spots for siege engines.) 
Over the years, a number of deficiencies, bugs and UX issues have been found. 
- Similar to the map editor, also the AIV editor has been augmented locally by some people via CE scripts, mostly providing hotkeys to navigate the AIV editor more effectively, but also providing some UX improvements and access to otherwise-inaccessible stuff. Integrating that in the AIV editor, or finding a good way to distribute it in a well-usable way would be nice. 
- The AIV editor currently lacks the ability to place troop spots for monks and tunnelers to the AIV editor, as those are missing entirely in the vanilla AIV editor UI. Also, oil pot engineers only have 9 spots (see [Feature request: Fix usage of oil pot engineer troop spots in AIV](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/31)), while siege engines currently have 10 spots but not all of them are usable (AI skips some of them, and crashes when trying to use the 10th spot). Providing support for 10 unit spots for all these would be great. 
- Extending the number of troop spots beyond 10 would also be cool. (Albeit that would likely require an internal data format adjustment, complicating things.)


## Communication and Guidance
We want to make the UCP, its features and general functionality, as well as cool user-generated content more well-known and accessible. The UCP already provides a ton of stuff (and a lot of it is by now even taken for granted / as a baseline for our community), but besides some videos of a few people using the UCP behind the scenes in some way (e.g. for AI battles), there's still rather little presence of it online, and for some aspects of the UCP, many people struggle to find adequate information. 
- Include more info stuff in the GUI directly, or embed/link to resources like explanation or showcase videos on YouTube about individual aspects. The last couple releases of UCP2 featured some images and GIFs to illustrate and showcase new features on the GitHub release pages. Something like this in the UCP3 GUI could help visualize how things work. 
- Generally, create more structured and modular videos, rather than trying to make a single 30min video "UCP tutorial for all the things" that many people have no time to watch, or may simply find to be outdated and ambiguous or obsolete soon after. 
- Also, a good UX-centered "UCP2 to UCP3" video might help people understand which "old and known" aspects of UCP2 correspond to what in UCP3. Not sure whether to best tackle this with a concise video, some info graphics or at least an additional FAQ section on the discord. 
- Add a feedback form / links (to discord's feedback section, to github issue sections) in the UCP GUI. 
- Guide people to the discord (and especially the help/faq resources available there) as well as the UCP website more prominently from the UCP GUI. (Currently you need to find the small banner inside the "credits" modal, and get no context what to expect on the discord; and the website is linked nowhere at all, iirc.)
- The first hurdle to new users is already finding the correct github repository and finding the correct download on there. For tech-savvy people, this is not an issue, but it happens often enough that people don’t find their way and require manual assistance. We can probably improve on this somehow? Can we also make the faq on the discord server more prominent for people who newly join the discord server? 
- Info graphics on certain things can go a long way, combining the static structure and persistence of texts with the visuality of images or tutorial videos. They can be used not only specifically to explain the UCP itself (e.g. "How To Create an Extension", "How To Use a Pack I heard of" or "How Feature XY works / Before-and-After"), but also certain aspects of the game (e.g. "Hotkeys", "Multiplayer caveats and troubleshooting", "Unit stances", or some mapmaking-related topics like all the "hidden" menus and map editor hotkeys, which most people still don't know about at all). \
Things like a proper "Hotkeys" overview... that's info that pro players may know by heart at some point, but it is still a valuable resource to new or casual players, making it more accessible to use these hotkeys by making people more aware of them (both for vanilla and possibly UCP-extended ones in the future). And generally speaking, this sort of thing can make all the difference between a feature getting used vs being ignored for quite many people. (In the year 2024, there's still people who are absolutely amazed after discovering they can simply press F1 in Freebuild mode to access a menu for spawning events and invasions, use number keys to set rally points for unit recruitment, press Ctrl+M to open the trading post menu, or even numpad +- to change the game speed.) \
<details><summary>Example: Settlers United ("the UCP for _Settlers IV_") uses this approach. You can open an infographic about the game's (SU-extended) Hotkeys in a separate window through the SU-Launcher. (**show image**)</summary>

![Settlers United Hotkeys Infographics](https://github.com/user-attachments/assets/892da70b-0a29-4fd4-8fca-c5c9b7020108)

</details>
- Tutorial / guide texts are currently few and far apart, spread across Github wiki pages, the UCP website and some discord channels. We should try and establish the wiki as a knowledge base where all relevant info can be found, and make sure the github wiki is more easily found by users from elsehwere (UCP GUI, Website, Discord). Writing and/or updating guides as well, ofc (AIC editing in particular!). 
- The UCP GUI itself currently is a bit of a "text monster" (just like this wiki page^^) that is all about reading and reading and reading, with very little to *look at* besides the Reconquista teaser header backdrop image. And with a lack of visualisation and built-in "help resources" in visual or also textual form, a lot of people are currently more confused or scared or overwhelmed than they'd have to be. 
- Guide people to the different github repos for creating issues

---