# Face Recognition Python\* Demo
Note : The model is a stripped down version of https://github.com/openvinotoolkit/open_model_zoo/blob/master/demos/face_recognition_demo/python/README.md
For more details please refer the above model

## Running

Running the application with the `-h` option or without
any arguments yields the following message:

```
usage: face_recognition_demo.py [-h] -i INPUT [--loop] [-o OUTPUT]
                                [-limit OUTPUT_LIMIT]
                                [--output_resolution OUTPUT_RESOLUTION]
                                [--no_show] [--crop_size CROP_SIZE CROP_SIZE]
                                [--match_algo {HUNGARIAN,MIN_DIST}]
                                [-u UTILIZATION_MONITORS] [-fg FG]
                                [--run_detector] [--allow_grow] -m_fd M_FD
                                -m_lm M_LM -m_reid M_REID
                                [--fd_input_size FD_INPUT_SIZE FD_INPUT_SIZE]
                                [-d_fd {CPU,GPU,MYRIAD,HETERO,HDDL}]
                                [-d_lm {CPU,GPU,MYRIAD,HETERO,HDDL}]
                                [-d_reid {CPU,GPU,MYRIAD,HETERO,HDDL}] [-v]
                                [-t_fd [0..1]] [-t_id [0..1]]
                                [-exp_r_fd NUMBER]

Optional arguments:
  -h, --help            Show this help message and exit.

General:
  -i INPUT, --input INPUT
                        Required. An input to process. The input must be a
                        single image, a folder of images, video file or camera id.
  --no_show             Optional. Don't show output.
  --crop_size CROP_SIZE
                        Optional. Crop the input stream to this resolution.
  --match_algo {HUNGARIAN,MIN_DIST}
                        Optional. Algorithm for face matching.
                        Default: HUNGARIAN.
                        
Faces database:
  -fg                   Optional. Path to the face images directory.
  --allow_grow          Optional. Flag to allow growing the face database,
                        in addition allow dumping new faces on disk. In that
                        case the user will be asked if he wants to add a
                        specific image to the images gallery (and it leads to
                        automatic dumping images to the same folder on disk).
                        If it is, then the user should specify the name for
                        the image in the open window and press `Enter`.
                        If it's not, then press `Escape`. The user may add
                        new images for the same person by setting the same
                        name in the open window.

Models:
  -m_fd PATH            Required. Path to an .xml file with Face Detection model.
  -m_lm PATH            Required. Path to an .xml file with Facial Landmarks Detection
                        model.
  -m_reid PATH          Required. Path to an .xml file with Face Reidentification
                        model.
  --fd_input_size FD_INPUT_SIZE
                        Optional. Specify the input size of detection model for
                        reshaping. Example: 500 700.

Inference options:
  -d_fd {CPU,GPU,MYRIAD,HETERO,HDDL}
                        Optional. Target device for Face Detection model.
                        Default value is CPU.
  -d_lm {CPU,GPU,MYRIAD,HETERO,HDDL}
                        Optional. Target device for Facial Landmarks Detection
                        model. Default value is CPU.
  -d_reid {CPU,GPU,MYRIAD,HETERO,HDDL}
                        Optional. Target device for Face Reidentification
                        model. Default value is CPU.
  -t_fd [0..1]          Optional. Probability threshold for face detections.
  -t_id [0..1]          Optional. Cosine distance threshold between two vectors
                        for face identification.
  -exp_r_fd NUMBER      Optional. Scaling ratio for bboxes passed to face
                        recognition.
```

Example of a valid command line to run the application:

Linux (`sh`, `bash`, ...) (assuming OpenVINO installed in `/opt/intel/openvino`):

``` sh
# Set up the environment
source /opt/intel/openvino/bin/setupvars.sh

# Run the model as
python3 face_recognition_demo.py \
  -i <path_to_video>/input_video.mp4 \
  -m_fd <path_to_model>/face-detection-retail-0004.xml \
  -m_lm <path_to_model>/landmarks-regression-retail-0009.xml \
  -m_reid <path_to_model>/face-reidentification-retail-0095.xml \
  -fg "<path_to_face_gallery/face_gallery" \
   --allow_grow \
```
