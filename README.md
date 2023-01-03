# URDF to OBJ
This repository contains a script that extracts all the `.obj` files from a Unified Robot Description Format (`URDF`) file and converts them into world frame coordinates. This is useful for importing a robot into a physically-based renderer like Blender or Mitsuba, as these programs do not currently support URDF files. 

## Requirements
This package was developed in Python 3.8+. The required libraries are:
- `numpy==1.22.3`
- `urdfpy==0.0.22`
- `trimesh==3.16.4`

## Usage
To use the script, clone this repository and run the following commands:

```
python urdf_to_obj.py --urdf_path relative/path/to/urdf
```
This extracts a single mesh and places it in `meshes_extracted/mesh_merged.obj`.

Additionally, we can extract individual `.obj` files. This is useful when we need multiple `.obj` files that can be later rotated and translated individually within a renderer (e.g. Mitsuba, Blender)

```
python urdf_to_obj.py --urdf_path relative/path/to/urdf --multiple_obj
```
This extract multiple `.obj` files and places them in `meshes_extracted/mesh_extracted_{INDEX}.obj`

## Example
To see how this works, simply run:
```
python urdf_to_obj.py --urdf_path 'urdf_files/ur5/tactip/ur5_with_standard_tactip.urdf' --multiple_obj
```
As a result, 11 individual components and a single emrged mesh defined in world frame are extracted into `meshes_extracted/'.

We can then import these filed in Blender and produce a pretty rendering:

# Note
This script only works for extracting `.obj` files. Other file types are not currently supported.

# References
If you find this useful, please consider citing:
```
@misc{comi2022active,
    author = {Mauro Comi},
    title = {{URDF to OBJ}},
    howpublished = {\url{https://github.com/maurock/urdf_to_obj}},
    year = {2023}
}
```
```
@software{trimesh,
	author = {{Dawson-Haggerty et al.}},
	title = {trimesh},
	url = {https://trimsh.org/},
	version = {3.2.0},
	date = {2019-12-8},
}
```


