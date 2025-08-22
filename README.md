<h1>Video Sharing Platform</h1>



<h2>Project Description</h2>

In this project, I will design a simplified version of a video-sharing platform. This platform will allow users to upload videos, store video metadata, process videos into multiple resolutions, analyze content for appropriateness, and serve videos to users with minimal latency.


<h2>Video Uploading Workflow</h2>

<img width="974" height="279" alt="image" src="https://github.com/user-attachments/assets/2d27673f-0b5b-43be-bd4c-09c20ff29054" />

Step 1:
The initial step in this workflow is a user uploading their video to YouTube. Usually, this video will be uploaded in 4K high quality. This video will be initially stored in S3 object storage, which is a great choice for video files.

Step 2:
Video metadata, which is general text based information about the video, like video title, video tags, or video description, needs to be stored. For free-form text data like this, a NoSQL database like OpenSearch would be an excellent choice. 

Step 3:
The video will be processed as it is uploaded. YouTube processes videos into multiple resolutions (360p, 720p, 1080p etc). These resolutions can be served to different users based on their requirements, as not all users can support high quality videos. Elemental MediaConvert would aid in this process.

Step 4:
Video analysis will be done with Rekognition. Rekognition uses machine learning to do automated content analysis to make sure videos uploaded aren't inappropriate. It scans video frames for inappropriate content, if it detects any, the videos will not be viewable by the public.

Step 5:
After the video is processed, it is stored in another S3 object storage, this time organized in different resolutions for streaming.

Step 6:
Finally, we serve content to users across the globe with CloudFront as a CDN. CloudFront caches video content at edge locations nearest to our users. The CDN reduces load time and provides a seamless viewing experience.
