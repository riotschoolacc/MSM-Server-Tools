Requests
-

* All requests are sent with atleast one (but not required) param, `(Long) last_updated`, which is the `(Long) last_updated` in their Cached version.

## Loading Screen Requests (None of these *require* params)

* db_monster - `Sends all Monster Data`

* db_gene - `Sends all Gene Data`

* db_bakery_foods - `Sends all Bakery Food Data`

* db_structure - `Sends all Structure Data`

* db_island_v2 - `Sends all Island Data`

* db_scratch_offs - `Sends all Scratch Minigame Data`

* db_attuner_gene - `Sends all Attuner Gene Data`

* gs_timed_events - `Sends all current Limited-Time Events`

* gs_rare_monster_data - `Sends all Monsters that are Rare`

* gs_epic_monster_data - `Sends all Monsters that are Epic`

* db_flexeggdefs - `Sends all Flex Egg Data`

* gs_flip_boards - `Sends all Memory Minigame Boards`

* gs_flip_levels - `Sends all Memory Minigame Level Data`

* gs_monster_island_2_island_data - `Not sure..`

* gs_cant_breed - `Sends all Monsters that cannot breed`

* db_battle - `Sends all Collosingum Data`

* db_battle_levels - `Sends all Collosingum Level Data`

* db_battle_monster_training - `Sends all Collosingum Monster Training Data`

* db_battle_monster_actions - `Sends all Collosingum Monster Actions`

* db_battle_monster_stats - `Sends all Collosingum Monster Statistics`

* db_battle_music - `Sends All Collosingum Music`

* db_costumes - `Sends all Costumes`

* gs_player - `Sends Player Data`

# Other Loading Screen Requests that aren't requested

* db_level - `Sends all Level data`

* gs_sticker - `Sends all Avatar data`

* gs_quest - `Sends all Quests the player hasn't completed`

# Test Requests (None of these *require* params)

* test_types - `Sends a test of all SFS Types`

# Deprecated Requests (None of these *require* params)

* gs_island (First version of *gs_island_v2*) - `Sends all Island Data`

# Ingame Requests
  
  ## Eggs (All of these require params)
  
  * gs_buy_egg - `Purchases a Monster egg`
    * params: `(int) monster_id,` (not required) `(bool) starpower_purchase`, (not required) `(long) nursery_id` 
  
  * gs_hatch_egg - `Hatches and places a Monster`
    * params: `(long) user_egg_id`, `(int) pos_x`, `(int) pos_y`, `(int) flip`
  
  * gs_sell_egg
    * params: `(long) user_monster_id`
  
  ## Monster (All of these require params)
  
  * gs_sell_monster - `Sells Monster to market`
    * params: `(long) user_monster_id`
  
  * gs_rename_monster - `Renames a Monster`
    * params: `(long) user_monster_id`, `(utf-string) name`
  
  * gs_move_monster - `Moves a Monsters position`
    * params: `(int) pos_x`, `(int) pos_y`, `(double) volume`, `(long) user_monster_id`
  
  * gs_flip_monster - `Flips a Monster`
    * params: `(long) user_monster_id`, `(bool) flipped`
  
  * gs_mute_monster - `Mutes a Monster`
    * params: `(long) user_monster_id`
  
  * gs_mega_monster_message - `Biggifys a Monster`
    * params: `(long) user_monster_id`, (not required) `(bool) mega_enable`
  
  * gs_collect_monster - `Collects a Monsters coins`
    * params: `(long) user_monster_id`
  
  ## Structure (All of these require params) 
  
  * gs_buy_structure - `Purchases a Structure`
    * params: `(int) pos_x`, `(int) pos_y`, `(double) scale`, `(int) structure_id`, `(int) flip`
  
  * gs_sell_structure - `Sells a Structure`
    * params: `(long) user_structure_id`
  
  * gs_start_upgrade_structure - `Starts upgrading a Structure`
    * params: `(long) user_structure_id`
  
  * gs_move_structure - `Moves a Structure`
    * params: `(int) pos_x`, `(int) pos_y`, `(double) scale`, `(long) user_structure_id`
  
  * gs_flip_structure - `Flips a structure`
    * params: `(long) user_structure_id`, `(bool) flipped`
  
  ## Island (All of these require params)
  
  * gs_change_island - `Changes current Island`
    * params: `(long) user_island_id`
  
  * gs_buy_island - `Buys an Island`
    * params: `(int) island_id`
  
  * gs_save_island_warp_speed - `Saves an Islands Time Machine Speed`
    * params: `(long) user_island_id`, `(double) warp_speed`
  
  * gs_refresh_tribe_requests - `Refreshes users Tribe join requests`
  
  ## Minigame (Most of these require params)
  
  * gs_player_has_scratch_off - `Checks if the player can play Scratch Minigame`
    * params: `(utf-string) type`
  
  * gs_play_scratch_off - `Sends Scratch Minigame data`
    * params: `(utf-string) type`
  
  * gs_purchase_scratch_off - `Purchases a round of the Scratch Minigame`
    * params: `(utf-string) type`, `(bool) requestFree`
  
  * gs_collect_scratch_off - `Collects Scratch Minigame Rewards`
    * params vary depending on `type`
  
  ## Account (All of these require params)
  
  * gs_set_displayname - `Sets Players Display Name`
    * params: `(utf-string) newName`
  
  ## Settings Page (All of these require params)

  * gs_referral_request - `Sends a Referral Request`
    * params: `(long) referring_bbb_id`

  ## Other
  
  * gs_get_code - `Not Sure`
    * params: `(utf-string) code` **Must have "R:" at the start**
