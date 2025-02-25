# aihub_news_labeling_project

# AI Hub 뉴스 대본 및 앵커 음성 데이터 처리

이 프로젝트는 **AI Hub의 "뉴스 대본 및 앵커 음성 데이터"**에서 **라벨링 데이터를 다운로드하고, 전사 텍스트를 추출 및 전처리하는 자동화 스크립트**입니다.

---
## 📌 **프로젝트 개요**
### ✅ **주요 기능**
1. **AI Hub 라벨링 데이터 다운로드**
   - AI Hub에서 `aihubshell`을 사용하여 **TL (Training) 및 VL (Validation) 데이터 다운로드**  
   - Windows에서 **PowerShell 스크립트**를 실행하여 Google Drive로 자동 업로드  
   
2. **Google Colab에서 데이터 처리**
   - Google Drive에서 데이터를 Colab으로 가져오고 **압축 해제**
   - TL & VL 디렉토리 내 **모든 JSON 파일 탐색**
   - **전사 텍스트(text_only.txt) 저장**
   - **전처리된 텍스트(text_preprocessed.txt) 저장**
   - JSON 파일의 **개수를 확인**

---
## 🚀 **실행 방법**
### 1️⃣ **Windows에서 AI Hub 데이터 다운로드**
Windows의 **PowerShell을 사용하여 AI Hub 데이터를 Google Drive로 업로드**합니다.

#### **🔹 실행 코드 (`upload_to_gdrive.ps1`)**
```powershell
# Google Drive 경로 설정 (Google Drive가 G 드라이브로 마운트되었다고 가정)
$drivePath = "G:\My Drive\AIHub_Data"
$localPath = "C:\Users\sammy\Desktop\AIHub_Data"

# Google Drive에 업로드할 폴더 생성
New-Item -ItemType Directory -Path $drivePath -Force

# 데이터 압축 후 Google Drive로 업로드
Compress-Archive -Path "$localPath\*" -DestinationPath "$drivePath\AIHub_Data.zip" -Force
Write-Host "✅ AIHub_Data.zip 파일이 Google Drive에 업로드되었습니다!"
