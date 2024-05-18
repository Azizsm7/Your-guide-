from pytube import YouTube

def download_video(url, save_path):
    try:
        yt = YouTube(url)
        video = yt.streams.filter(progressive=True, file_extension='mp4').first()
        video.download(save_path)
        print("Download successful!")
    except Exception as e:
        print(f"Error downloading video: {e}")

# Example usage:
urls = [
    "https://www.youtube.com/watch?v=VIDEO_ID",
    "https://www.facebook.com/PAGE_NAME/videos/VIDEO_ID",
    "https://www.instagram.com/p/VIDEO_ID/",
    # Add more social media video URLs as needed
]

save_path = "/path/to/save/videos/"

for url in urls:
    download_video(url, save_path)
