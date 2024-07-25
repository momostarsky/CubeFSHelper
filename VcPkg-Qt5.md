1.需要执行 pip3 install jinja2   
2.安装     sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev


## VTK
```text

find_package(VTK REQUIRED)

target_link_libraries(main PRIVATE ${VTK_LIBRARIES})


find_package(VTKm CONFIG REQUIRED)

target_link_libraries(main PRIVATE vtkm::io vtkm::diy vtkm::lcl vtkm::cont)
```
