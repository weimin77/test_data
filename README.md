# test_data

测试数据集合仓库。每个数据集单独占用一个顶层文件夹，互不干扰。

## 目录

| 文件夹 | 内容 | 来源 | 大小 |
| --- | --- | --- | --- |
| [`opencv-samples/`](opencv-samples/) | OpenCV 官方示例数据（立体匹配图像对、标定板、视频等） | [opencv/opencv](https://github.com/opencv/opencv) 分支 `4.x`，commit `57a9702` | 22 MB |
| [`stereo/`](stereo/) | Middlebury 立体匹配基准数据集（2001 / 2003 / 2005 / 2006 / 2014） | [vision.middlebury.edu/stereo](https://vision.middlebury.edu/stereo/) | 723 MB |

## opencv-samples

从 OpenCV 主仓库以 sparse checkout 方式取出 `samples/` 目录，保留了上游的目录结构和
`LICENSE` / `COPYRIGHT`。主要可用数据位于 `opencv-samples/samples/data/`，例如：

- 立体匹配图像对：`aloeL.jpg` / `aloeR.jpg`（含真值 `aloeGT.png`）、
  `left.jpg` / `right.jpg`
- 双目标定序列：`left01.jpg`–`left14.jpg`、`right01.jpg`–`right09.jpg`，配合
  `stereo_calib.xml`、`intrinsics.yml`、`left_intrinsics.yml`、`calibration.yml`
- 其他：`chessboard.png`、`board.jpg`、`H1to3p.xml`、`aruco/`、
  视频 `vtest.avi` / `tree.avi` / `Megamind.avi`

`opencv-samples/` 内的 `.gitignore` 与 `.gitattributes` 来自上游仓库，仅作用于该子目录，
不影响本仓库其他文件夹。

## stereo

Middlebury Stereo 基准数据集，保留原始的 `Middlebury Stereo Datasets/<年份>/<场景>/` 层级。
只包含**官方发布的数据**，不含任何转换或派生产物。

| 年份 | 场景数 | 体积 | 说明 |
| --- | --- | --- | --- |
| 2001 | 7 | 30 MB | `barn1` `barn2` `bull` `poster` `sawtooth` `tsukuba` `venus`，多视角 PPM + PGM 视差 |
| 2003 | 4 | 44 MB | `cones` `conesF` `teddy` `teddyF` |
| 2005 | 9 | 4.9 MB | `Art` `Books` `Computer` `Dolls` `Drumsticks` … |
| 2006 | 21 | 11 MB | `Aloe` `Baby1`–`Baby3` `Bowling1/2` `Cloth1`–`Cloth4` `Flowerpots` `Lampshade1/2` `Midd1/2` `Monopoly` `Plastic` `Rocks1/2` `Wood1/2` |
| 2014 | 10 | 635 MB | `Adirondack` `Backpack` `Bicycle1` `Cable` `Classroom1` `Couch` `Flowers` `Jadeplant` `Mask` `Motorcycle`，均带 `-perfect` 后缀 |

2014 每个场景包含（2880×1988）：

- `im0.png` / `im1.png` — 已校正的左右视图
- `im1E.png` / `im1L.png` — 右视图的曝光/光照变体
- `disp0.pfm` / `disp1.pfm` — 左右视图的浮点视差真值（PFM，float32，单位：像素）
- `calib.txt` — `cam0`/`cam1` 内参、`baseline`、`doffs`、`ndisp`、`vmin`/`vmax`

较早年份的文件名与格式不同：

- 2001：`scene1.row3.col1.ppm`–`.col5.ppm` 多视角影像 + `truedisp.row3.col3.pgm` 真值，
  另有 `disp.png` / `rgb.png` 预览
- 2003：`im2.png` / `im6.png` + `disp2.png` / `disp6.png`
- 2005 / 2006：`view1.png` / `view5.png` + `disp1.png` / `disp5.png`（2005 的 `Art`
  额外带 `xxx_depth.png`）

> 生成物（点云 `*_cloud_m.ply`、16 位 PNG 视差、`-sd`/`-n` 变体）**未包含**在此仓库中，
> 它们可由 `disp0.pfm` + `im0.png` 重新计算得到。

## 许可

- `opencv-samples/`：遵循 OpenCV 的 3-clause BSD 许可，见
  [`opencv-samples/LICENSE`](opencv-samples/LICENSE)。
- `stereo/`：Middlebury 数据集的原始使用条款见
  [vision.middlebury.edu/stereo](https://vision.middlebury.edu/stereo/)，
  仅限研究与学术用途。

## 新增数据集

新建一个顶层文件夹存放数据，并在上面的表格中追加一行，说明来源、版本和体积。
