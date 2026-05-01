```
set_app_options -name route.global.timing_driven -value true
set_app_options -name route.global.crosstalk_driven -value true
set_app_options -name route.track.timing_driven -value true
set_app_options -name route.track.crosstalk_driven -value true
set_app_options -name route.detail.timing_driven -value true
```

```
set_app_options -name route.detail.antenna -value true
set_app_options -name route.detail.antenna_fixing_preference -value use_diodes
set_app_options -block [current_design] -name route.detail.diode_libcell_names -value {*/ANTENNA_RVT}
```

```
route_global
```

```
route_track
```

```
route_detail
```
```
set_app_options -name route_opt.flow.enable_ccd -value true
route_opt
```
```
write_lef $LEF_FILE
write_parasitics -format spef -output $SPEF_FILE
write_verilog $routed_netlist
write_sdc -output $SDC_FILE
```
```
report_timing -scenario func_slow -delay_type max
```
```
report_timing -scenario func_slow -delay_type min
```

