<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>비디오 플레이어</title>
</head>
<body>
    <h1>비디오 플레이어</h1>
    
    <!-- 비디오 링크 입력 폼 -->
    <form>
        <label for="videoLink">비디오 링크 입력:</label><br>
        <input type="text" id="videoLink" name="videoLink" placeholder="유튜브 또는 구글 드라이브 비디오 링크 입력"><br><br>
        <button type="button" onclick="playVideo()">비디오 재생</button>
    </form>
    
    <!-- 비디오 플레이어 -->
    <div id="videoPlayer"></div>

    <script>
        function playVideo() {
            var videoLink = document.getElementById("videoLink").value;
            var videoPlayer = document.getElementById("videoPlayer");

            // YouTube 링크일 경우
            if (videoLink.includes("youtube.com")) {
                var videoId = videoLink.split("v=")[1];
                var embedUrl = "https://www.youtube.com/embed/" + videoId;
                videoPlayer.innerHTML = "<iframe width='560' height='315' src='" + embedUrl + "' frameborder='0' allowfullscreen></iframe>";
            } 
            // 구글 드라이브 링크일 경우
            else if (videoLink.includes("drive.google.com")) {
                var fileId = videoLink.split("id=")[1];
                var embedUrl = "https://drive.google.com/file/d/" + fileId + "/preview";
                videoPlayer.innerHTML = "<iframe src='" + embedUrl + "' width='560' height='315' frameborder='0' allowfullscreen></iframe>";
            } 
            // 다른 링크 형식일 경우
            else {
                alert("유효한 비디오 링크를 입력하세요.");
            }
        }
    </script>
</body>
</html>
