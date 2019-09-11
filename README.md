# FFmpeg
----

## Getting Start
* 好きな動画ファイルを files/ に格納
* $ docker-compose up -d

#### 動画の情報を閲覧
* $ docker-compose exec ffmpeg ffmpeg -i files/yourvideo.mp4

#### 動画を変換
**FLV形式の動画をMP4形式に変換する**
* $ docker-compose exec ffmpeg ffmpeg -i input.flv output.mp4

**MP4形式の動画をAVI形式に変換する**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 output.avi

**MP4形式の動画をコーディックH.265のMP4形式の動画に変換する**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 -vcodec libx265 output.mp4

**MP4形式の動画をビットレート340kbpsのMP4形式の動画に変換する**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 -vb 340k output.mp4

**MP4形式の動画をフレームレート120fpsのMP4形式の動画に変換する**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 -r 120 output.mp4

#### 連番画像から動画を作る
`image001.png` `image002.png` `image003.png` … `imageXXX.png` と連番の画像から動画ファイルを作りたいとき

**連番ファイルからmacで再生できる動画をつくる**
* $ docker-compose exec ffmpeg ffmpeg -i image%03d.png -pix_fmt yuv420p output.mp4

**60fpsの連番ファイルから動画をつくる**
* $ docker-compose exec ffmpeg ffmpeg -r 60 -i image%03d.png output.mp4

#### 連番画像から動画を作る
**動画から連番ファイルをつくる**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 image%03d.png

**動画から1秒あたり60枚の連番ファイルをつくる**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 -r 60 image%03d.png

#### 動画をgifに変換
**動画をアスペクト比を保ったまま横幅640ピクセルにリサイズ、フレームレートは10fpsでgifに変換**
* $ docker-compose exec ffmpeg ffmpeg -i input.mp4 -vf scale=640:-1 -r 10 output.gif


参考：https://qiita.com/cha84rakanal/items/e84fe4eb6fbe2ae13fd8