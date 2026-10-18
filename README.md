# CSRT-OBJECT-TRACKING
Object tracking in video with OpenCV’s CSRT tracker, with per-frame FPS and success-rate analysis. Python, Google Colab.

A Google Colab notebook that tracks a user-selected object through a video
using OpenCV's CSRT (Channel and Spatial Reliability Tracking) algorithm,
and evaluates the run with quantitative metrics.

## How it works
1. Load and validate a video (resolution, frame count, FPS, duration).
2. Display the first frame with a coordinate grid to pick the target's bounding box.
3. Initialize the CSRT tracker and process the video frame by frame,
   with a progress bar and periodic visual previews.
4. Plot the results: FPS over time, tracking vs. lost time, and a summary table.

## Metrics
- Per-frame processing time and FPS (mean / min / max)
- Tracked vs. lost frames and tracking rate
- Time spent tracking vs. lost

## Results
On a self-recorded test video (492 frames), the tracker kept the target in
every frame (100% tracking rate) at an average of ~6.2 FPS on Colab (CPU).
Note: CSRT reports success even when it drifts, so results were also
verified visually on preview frames.

## Usage
1. Open `projectCode.ipynb` in Google Colab.
2. Upload your video to `/content/` and set `VIDEO_PATH`.
3. Run Cell 4 to inspect the first frame and choose `BBOX = (x, y, w, h)`.
4. Run the remaining cells top to bottom.

## Tech stack
Python, OpenCV (opencv-contrib), NumPy, Matplotlib

## Limitations
CSRT degrades with fast motion, large scale changes, and full occlusion,
and has no built-in re-detection after the target is lost.
