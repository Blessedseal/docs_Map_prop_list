# KV Table

{% tabs %}
{% tab title="All Gamemodes" %}
| Name                       | Type   | Notes                                               |
| -------------------------- | ------ | --------------------------------------------------- |
| `min_players`              | `int`  | Minimum number of players required to start a match |
| `max_players`              | `int`  | Maximum player limit                                |
| `max_team_players`         | `int`  | Maximum number of players in a team                 |
| `match_ending_enabled`     | `bool` | Champion screen                                     |
| `skydive_ziplines_enabled` | `bool` | Activating ziplines                                 |
| `survival_jumpkit_enabled` | `bool` | Double jump Mode                                    |
| `survival_wallrun_enabled` | `bool` | Wallrun mode                                        |
| `survival_infinite_ammo`   | `bool` | Unlimited ammo for all weapons                      |
| `ground_loot_enable`       | `bool` | Whether loot should spawn on the ground             |
| `lootbin_loot_enable`      | `bool` | Whether loot should spawn in loot bins              |
{% endtab %}

{% tab title="Custom TDM" %}
| Name                   | Type     | \`                                                                                                                                                                                 |
| ---------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `replay_enabled`       | `bool`   | Whether kill replay should be enabled or not                                                                                                                                       |
| `replay_delay`         | `float`  | How far back do you want the replay to go                                                                                                                                          |
| `default_shield_hp`    | `float`  | <p>How much shield you spawn with. Shield type autoscales.</p><p>e.g. <code>75</code> for a blue shield</p>                                                                        |
| `whitelisted_weapon_x` | `string` | <p>If you want to restrict what weapons players can get, include the name of the weapons</p><p></p><p>Example KV: <code>whitelisted_weapon_0 "mp_weapon_mastiff"</code></p>        |
| `oob_damage_percent`   | `float`  | <p>How much ring should damage you if you go outside the bubble encompassing the play area</p><p>e.g. <code>25</code> to deal 25 health damage on a target with 100 max health</p> |
| `tgive_enabled`        | `bool`   | Whether you can give yourself weapons through `tgive`                                                                                                                              |
|                        |          |                                                                                                                                                                                    |
{% endtab %}
{% endtabs %}
