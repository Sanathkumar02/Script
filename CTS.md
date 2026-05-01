```
check_design -checks pre_clock_tree_stage
```
```
set_scenario_status func_slow -hold true -setup true -leakage_power true \
  -max_capacitance true -min_capacitance true -dynamic_power true \
  -max_transition true -active true
```
```
set_clock_routing_rules -min_routing_layer M3 -max_routing_layer M4 -default_rule
```
```
synthesize_clock_trees
```
```
clock_opt
```
