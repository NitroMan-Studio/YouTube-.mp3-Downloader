# YouTube-.mp3-Downloader
Small system console application for downloading sound files in .mp3 from YouTube

import youtube_dl


def run():
    video_url = str(input("Provide YouTube link: "))
    video_info = youtube_dl.YoutubeDL().extract_info(url=video_url, download=False)

    filename = f"{video_info['title']}.mp3"
    options = {'format': 'bestaudio/best', 'keepvideo': False, 'outtmpl': filename}
    with youtube_dl.YoutubeDL(options) as ydl:
        ydl.download([video_info['webpage_url']])

    print("Downloading done... {}".format(filename))


if __name__ == '__main__':
    run()
