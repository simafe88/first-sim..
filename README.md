# Install & load packages
if (!require(jpeg)) install.packages("jpeg", dependencies = TRUE)
if (!require(ggplot2)) install.packages("ggplot2", dependencies = TRUE)
if (!require(grid)) install.packages("grid", dependencies = TRUE)

library(jpeg)
library(ggplot2)
library(grid)

# ---- Load MRI image (replace with your own file) ----
img_path <- "brain_mri.jpg"   # put your MRI image in the working directory
mri_img <- readJPEG(img_path)

# ---- Example landmarks (x,y coordinates as % of image size) ----
landmarks <- data.frame(
  x = c(0.3, 0.5, 0.7, 0.5),   # relative positions (0-1)
  y = c(0.7, 0.5, 0.7, 0.3),
  label = c("Left Hemisphere", "Center", "Right Hemisphere", "Brainstem")
)

# ---- Plot image + landmarks ----
ggplot() +
  annotation_raster(mri_img, xmin = 0, xmax = 1, ymin = 0, ymax = 1) +
  geom_point(data = landmarks, aes(x = x, y = y), color = "red", size = 4) +
  geom_text(data = landmarks, aes(x = x, y = y, label = label), vjust = -1, color = "yellow") +
  labs(title = "MRI Brain Landmarks (Demo)") +
  theme_void()

# first-sim..
just testing
