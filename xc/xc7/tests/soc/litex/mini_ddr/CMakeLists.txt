add_file_target(FILE mem.init)
add_file_target(FILE mem_1.init)

add_file_target(FILE arty.sdc)
add_file_target(FILE arty_clocks.xdc)

get_target_property_required(PYTHON3 env PYTHON3)
get_target_property(PYTHON3_TARGET env PYTHON3_TARGET)

add_fpga_target(
  NAME minilitex_ddr_arty
  BOARD arty-full
  SOURCES
    minilitex_ddr_arty.v
    VexRiscv_Lite.v
  INPUT_IO_FILE arty.pcf
  INPUT_XDC_FILE minilitex_ddr_arty.xdc
  SDC_FILE arty.sdc
)

add_vivado_target(
    NAME minilitex_ddr_arty_vivado
    PARENT_NAME minilitex_ddr_arty
    XDC arty_clocks.xdc
)
