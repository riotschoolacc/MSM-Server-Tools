Requests
-

* All requests are sent with atleast one (but not required) param, `(Long) last_updated`, which is the `(Long) last_updated` in their cached version.

## Loading Screen Requests (None of these *require* params)

* db_monster

* db_gene

* db_bakery_foods

* db_structure

* db_island_v2

* db_scratch_offs

* db_attuner_gene

* gs_quest

* gs_timed_events

* gs_rare_monster_data

* gs_epic_monster_data

* db_flexeggdefs

* gs_flip_boards

* gs_flip_levels

* gs_monster_island_2_island_data

* gs_cant_breed

* db_battle

* db_battle_levels

* db_battle_monster_training

* db_battle_monster_actions

* db_battle_monster_stats

* db_battle_music

* db_costumes

* gs_player


# Unused and/or Test Requests (None of these *require* params)

* test_types - `responds with a test of all SFS Types`

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

* gs_rename_monster - `Renames Monster`
  * params: `(long) user_monster_id`, `(utf-string) name`

* gs_move_monster - `Moves Monsters position`
  * params: `(int) pos_x`, `(int) pos_y`, `(double) volume`, `(long) user_monster_id`

* gs_flip_monster - `Flips a Monster`
  * params: `(long) user_monster_id`, `(bool) flipped`

* gs_mute_monster - `Mutes a Monster`
  * params: `(long) user_monster_id`

* gs_scale_monster - `Biggifys a Monster`
  * params: `(long) user_monster_id`, (not required) `(bool) mega_enable`

* gs_collect_monster - `Collects Monsters coins`
  * params: `(long) user_monster_id`

## Structure (All of these require params) 

* gs_buy_structure

* gs_sell_structure
 
  * params: `(int) user_structure_id`

* gs_start_upgrade_structure - `Starts Upgrading Structure`
  * params: `(int) user_structure_id`

## Island (All of these require params)

* gs_change_island - `Changes current Island`
  * params: `(int) user_island_id`

* gs_buy_island - `Buys Island`
  * params: `(int) island_id`

* gs_save_island_warp_speed - `Saves Island Time Machine Speed`
  * params: `(int) user_island_id`, `(double) warp_speed`

* gs_refresh_tribe_requests - `Refreshes users Tribe join requests`

## Minigame (Most of these require params)

* gs_player_has_scratch_off - `Checks if player is able to play Scratch Minigame`
  * params: `(utf-string) type`

* gs_play_scratch_off - `Sends Scratch Minigame data`
  * params: `(utf-string) type`

* gs_purchase_scratch_off - `Purchases a round of the Scratch Minigame`
  * params: `(utf-string) type`, `(bool) requestFree`

* gs_collect_scratch_off
  * params varie depending on `type`

## Account (Most of these require params)

* gs_set_displayname
 
* gs_player - `Sends player data`
  * No Params

## Settings (All of these require params)

* gs_get_code - `For sending referral codes`
  * params: `(utf-string) code` **Must have "R:" at the start**
