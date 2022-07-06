# ffmpeg-usage-examples
ffmpeg usage examples

## Install
'sudo apt install ffmpeg'

## Cut a piece from the video
`ffmpeg -i input.mp4 -ss 00:00:50 -codec copy -t 50 output.mp4`,
- -ss 00:00:50 - start from 00:00:50
- -t 50 - time 50 sec

## Cut the video into two parts
`ffmpeg -i input.mp4 -t 00:00:30 -c copy part1.mp4 -ss 00:00:30 -codec copy part2.mp4`
- part1.mp4 - from 00:00:00 to 00:00:30
- part2.mp4 - from 00:00:30 to end of input.mp4

## Remove audio from video
`ffmpeg -i input.mp4 -vcodec copy -an output.mp4`

## Add audio to video
`ffmpeg -i input.mp4 -i zvuk.mp3 -vcodec copy -acodec copy output.mp4`

## mov to mp4 with quality preservation
`ffmpeg -i 'input.mov' -q:v 1 output.mp4`
- -q:v n, 1 < n < 31, 1 - the highest quality

## Photo banner for audio
`ffmpeg -loop 1 -i 001.jpg -i 001.mp3 -c:v libx264 -c:a copy -t 5 output.mp4`

## Stabilize the video
1. `ffmpeg -i input.mp4 -vf vidstabdetect=shakiness=5 stage1.mp4`
2. `ffmpeg -i stage1.mp4 -vf vidstabtransform output.mp4`

## Two videos side by side
`ffmpeg -i ' left.mp4' -i right.mp4 -filter_complex hstack -c:v libx264 output.mp4`
