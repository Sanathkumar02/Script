```
read_sdc -echo $SDC_PATH
```
```
set_app_options -name place.coarse.continue_on_missing_scandef -value true
set_app_options -name place_opt.flow.enable_ccd -value true
set_app_options -name place_opt.flow.clock_aware_placement -value true
set_app_options -name place_opt.place.congestion_effort -value high
```
```
set mode1 "func"
set corner1 "slow"
set scenario "${mode1}_${corner1}"
create_mode $mode1
create_corner $corner1
create_scenario -name $scenario -mode $mode1 -corner $corner1
```
```
set parasitic "p0"
read_parasitic_tech \
  -tlup "/data/pdk/pdk32nm/SAED32_EDK/tech/star_rcxt/saed32nm_1p9m_Cmax.tluplus" \
  -layermap "/data/pdk/pdk32nm/SAED32_EDK/tech/star_rcxt/saed32nm_tf_itf_tluplus.map" \
  -name p0

set_parasitic_parameters -late_spec $parasitic -early_spec $parasitic
```
```
create_placement -effort high
```
set_dont_use [get_lib_cells */*HADD*]
set_dont_use [get_lib_cells */MUX*]
set_dont_use [get_lib_cells */AO*]
set_dont_use [get_lib_cells */OA*]
set_dont_use [get_lib_cells */NAND*]
set_dont_use [get_lib_cells */XOR*]
set_dont_use [get_lib_cells */NOR*]
set_dont_use [get_lib_cells */XNOR*]
set_dont_use [get_lib_cells */FADD*]
```
```
set_scenario_status func_slow \
  -hold true -setup true \
  -leakage_power true -max_capacitance true \
  -min_capacitance true -dynamic_power true \
  -max_transition true -active true
 ```
```
place_opt
```
```
legalize_placement
```

