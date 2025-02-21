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

* gs_buy_egg

  * params: `(int) monster_id,` (not required) `(bool) starpower_purchase`

* gs_hatch_egg

  * params: `(int) user_egg_id`

* gs_sell_egg

  * params: `(int) user_monster_id`

## Monster (All of these require params)

* gs_sell_monster

  * params: `(int) user_monster_id`

* gs_rename_monster

* gs_move_monster

## Structure (All of these require params) 

* gs_buy_structure

* gs_sell_structure
 
  * params: `(int) user_structure_id`
