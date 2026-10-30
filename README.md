# test_data

测试数据集合仓库。每个数据集单独占用一个顶层文件夹，互不干扰。

## 目录

| 文件夹 | 内容 | 来源 | 大小 |
| --- | --- | --- | --- |
| [`opencv-samples/`](opencv-samples/) | OpenCV 官方示例数据（立体匹配图像对、标定板、视频等） | [opencv/opencv](https://github.com/opencv/opencv) 分支 `4.x`，commit `57a9702` | 22 MB |

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

## 许可

`opencv-samples/` 下的内容遵循 OpenCV 的 3-clause BSD 许可，见
[`opencv-samples/LICENSE`](opencv-samples/LICENSE)。

## 新增数据集

新建一个顶层文件夹存放数据，并在上面的表格中追加一行，说明来源、版本和体积。
