```
set PDK_PATH /data/pdk/pdk32nm/SAED32_EDK
create_lib -ref_libs "$PDK_PATH/lib/stdcell_rvt/ndm/saed32rvt_c.ndm"    FULLADDER
read_verilog {./results/full_adder.mapped.v} -top full_adder -design full_adder -library FULLADDER
link_block
start_gui
```
```
check_design -checks dp_pre_floorplan

```
```
initialize_floorplan -core_offset 3.5

```

