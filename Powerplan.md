```
connect_pg_net -pg -automatic
```

```
create_shape -shape_type rect -layer M7 -boundary {{0 3.5} {1.9 4.2}} -port VSS
create_shape -shape_type rect -layer M7 -boundary {{0 4.5} {3.15 5.4}} -port VDD

```


```
create_pg_ring_pattern core_ring \
  -horizontal_layer M7 -horizontal_width 0.7 -horizontal_spacing 0.4 \
  -vertical_layer M8 -vertical_width 0.8 -vertical_spacing 0.4
  ```


```
set_pg_strategy ring_stratergy -core \
  -pattern {{name:core_ring} {nets:{VDD VSS}} {offset:{0.5 0.5}}}
```


```
compile_pg -strategies ring_stratergy
```


```
create_pg_mesh_pattern mesh \
  -layers {
    {{vertical_layer:M6} {width:0.38} {spacing:interleaving} {pitch:1.3} {offset:0.45}} 
    {{horizontal_layer:M5} {width:0.34} {spacing:interleaving} {pitch:1} {offset:0.45}}
  }
```


```
set_pg_strategy core_mesh -pattern {{pattern:mesh} {nets:VDD VSS}} \
  -extension {stop:innermost_ring} -core
  ```
```
compile_pg -strategies core_mesh
```
```
create_pg_std_cell_conn_pattern std_cell_rail -layers {M1} -rail_width 0.8
```
```
set_pg_strategy rail_stratergy -core -pattern {{name:std_cell_rail} {nets:VDD VSS}}
compile_pg -strategies rail_stratergy
```

```
check_pg_connectivity
check_pg_drc
check_pg_missing_vias :
```

