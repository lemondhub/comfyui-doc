# 使用 ComfyUI 創建你的第一張 AI 圖片

大概兩年多前第一次使用 ChatGPT，兩年後的現在，我已經很習慣在開發東西時與 AI 一起合作。本以為這已經是 AI 能帶給我的最大衝擊，直到第一次看到用 AI 生成圖片。網路上展示的效果令人驚豔，但我屬於沒用過就不相信的人。稍微摸索後，我發現這些工具雖然還不到 "成神" 的地步，但 AI 圖片生成的能力給我的震撼，完全不亞於第一次使用 ChatGPT 的感受。

因此，我決定將實作過程記錄下來，既作為自己的筆記，也為對學習新工具感興趣的朋友提供參考。第一次接觸新工具總是比較痛苦，建議遇到看不懂的專有名詞先記下來，不要慌張，按步驟完成第一張圖。後續再回頭理解那些名詞時，會輕鬆許多。好了，讓我們從生成第一張圖片開始吧！

![第一張AI圖](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550417/%E7%AC%AC%E4%B8%80%E5%BC%B5AI%E5%9C%96_zma3jh.png)

---

## 安裝 ComfyUI

### 安裝 ComfyUI 的基本需求

1. **安裝 Python**  
   請下載 Python，如果打算安裝conda，請隨意選擇版本下載，如不使用Conda建議使用 3.10 版本（這是我個人選用的Conda ComfyUI python版本）：
   [Python 下載頁面](https://www.python.org/downloads/release/python-31013/)

![安裝Python](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E5%AE%89%E8%A3%9DPython_u8lfdv.png)

1. **安裝 Git**  
   下載並安裝 Git：[Git 官方網站](https://git-scm.com/)

![安裝Git](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E5%AE%89%E8%A3%9DGit_bamn8q.png)

1. **建議安裝 Conda**  
   Conda 可方便地管理 Python 環境，可以安裝 Miniconda：[Miniconda 官方網站](https://www.anaconda.com/download/success)

![安裝Conda](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/%E5%AE%89%E8%A3%9DConda_oczcdu.png)

### 安裝 ComfyUI 的具體步驟

1. **啟動終端機（Terminal）**

![啟動終端機](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550421/%E5%95%9F%E5%8B%95%E7%B5%82%E7%AB%AF%E6%A9%9F_sbkkvr.png)

1. **如果使用 Conda**  
   在終端機（Terminal）中輸入以下指令建立新的 Conda 環境：

   ```bash
   conda create -n comfyui_env python=3.10
   ```

   - `comfyui_env` 是環境名稱，可自行定義。
   - `python=3.10` 是 ComfyUI 建議使用的 Python 版本。

   接著，切換到新建的環境：

   ```bash
   conda activate comfyui_env
   ```

   **如果沒使用 Conda**  
   直接跳過 Conda 部分，從下一步開始，但是我很建議使用。

![建立新 Conda 環境](https://res.cloudinary.com/dev7ziixx/image/upload/v1735552409/%E5%BB%BA%E7%AB%8B%E6%96%B0Conda%E7%92%B0%E5%A2%83_dbv2a5.png)

1. **安裝 PyTorch**  
   根據顯示卡的 CUDA 版本安裝對應的 PyTorch。

   - 若你不確定 CUDA 版本，可以向 ChatGPT 詢問，或參考 [PyTorch 官方頁面](https://pytorch.org/get-started/locally/) 確認指令。
   - 以下為安裝 CUDA 11.8 版本的 PyTorch：

   ```bash
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
   ```

   > **注意：** 如果你的 GPU 不支援 CUDA 或沒有顯示卡，可以安裝 CPU-only 版本：
   > ```bash
   > pip install torch torchvision torchaudio
   > ```

![安裝 PyTorch](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550420/%E5%AE%89%E8%A3%9DPyTorch_bq1oae.png)

1. **使用 Git 下載 ComfyUI**  
   輸入以下指令下載 ComfyUI：

   ```bash
   git clone https://github.com/comfyanonymous/ComfyUI.git
   ```

![Git 下載 ComfyUI](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/Git%E4%B8%8B%E8%BC%89ComfyUI_jhursg.png)

1. 在終端機（Terminal）中切換到 ComfyUI 目錄：

   ```bash
   cd ComfyUI
   ```

   > **提示：** 如果安裝時更改過路徑，請確保進入正確的 ComfyUI 資料夾。

![切換到 ComfyUI 目錄](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E5%88%87%E6%8F%9B%E5%88%B0ComfyUI%E7%9B%AE%E9%8C%84_iddn9q.png)

1. 安裝 ComfyUI 相關程式：

   ```bash
   pip install -r requirements.txt
   ```

![安裝 ComfyUI 相關程式](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E5%AE%89%E8%A3%9DComfyUI%E7%9B%B8%E9%97%9C%E7%A8%8B%E5%BC%8F_pcnm4n.png)

---

## 啟動 ComfyUI

1. 在確認終端機（Terminal）正在ComfyUI的資料夾後，運行 ComfyUI 伺服器：

   ```bash
   python main.py
   ```

![運行 ComfyUI 伺服器](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E9%81%8B%E8%A1%8CComfyUI%E4%BC%BA%E6%9C%8D%E5%99%A8_fanshm.png)

1. 打開瀏覽器（如 Chrome、Safari），在地址欄輸入以下網址：

   ```
   http://127.0.0.1:8188
   ```

   這樣就能啟動 ComfyUI 的介面。

![啟動 ComfyUI](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550422/%E5%95%9F%E5%8B%95ComfyUI_bm6vf2.png)

---

## 初次運行 ComfyUI

1. **第一次運行**  
   ComfyUI 啟動後會顯示範例預設設定。點選 **Queue** 即可嘗試運行。

![第一次運行](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/%E7%AC%AC%E4%B8%80%E6%AC%A1%E9%81%8B%E8%A1%8C_o5qa9n.png)

1. **第一個錯誤**  
   如果直接運行出現錯誤，是因為新安裝的 ComfyUI 沒有任何模型，需要手動下載模型。

![第一個錯誤](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/%E7%AC%AC%E4%B8%80%E5%80%8B%E9%8C%AF%E8%AA%A4_edddzd.png)

1. **下載模型**  
   ComfyUI 預設的 checkpoint 名為 `v1-5-pruned-emaonly.ckpt`。可從 [Hugging Face](https://huggingface.co/) 下載：
   [下載連結](https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/blob/main/v1-5-pruned-emaonly.ckpt)

![下載模型](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550417/%E4%B8%8B%E8%BC%89%E6%A8%A1%E5%9E%8B_i5pkjc.png)

1. **放置模型檔案**  
   將 `v1-5-pruned-emaonly.ckpt` 文件放置在 ComfyUI 資料夾的以下路徑：

   ```
   comfyUI/models/checkpoints/
   ```

   > **注意：** 如果該路徑不存在，需手動創建對應的資料夾。

![放置模型檔案](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550422/%E6%94%BE%E7%BD%AE%E6%A8%A1%E5%9E%8B%E6%AA%94%E6%A1%88_zewc9m.png)

1. **重啟 ComfyUI**  
   模型放置好後，重新啟動 ComfyUI：
   - 在終端機（Terminal）中按下 `Ctrl + C` 關閉伺服器。
   - 再次輸入以下指令啟動 ComfyUI：

   ```bash
   python main.py
   ```

![重啟 ComfyUI](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550420/%E9%87%8D%E5%95%9FComfyUI_yfq60v.png)

1. **選擇模型**  
   在 ComfyUI 的 checkpoint 選單中，選取剛下載的 `v1-5-pruned-emaonly.ckpt`。

![選擇模型](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550419/%E9%81%B8%E6%93%87%E6%A8%A1%E5%9E%8B_h5mnne.png)

1. **生成第一張圖片**  
   點選 **Queue**，即可生成你的第一張圖片！

![生成第一張圖](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/%E7%94%9F%E6%88%90%E7%AC%AC%E4%B8%80%E5%BC%B5%E5%9C%96_ugusbj.png)

---

## 再次啟動 ComfyUI

如果你有使用 Conda，請記得在重新啟動終端機（Terminal）時確認啟用正確的 Conda 環境：

```bash
conda activate comfyui_env
cd ComfyUI
python main.py
```

![再次啟動 ComfyUI](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550418/%E5%86%8D%E6%AC%A1%E5%95%9F%E5%8B%95ComfyUI_jzk5qi.png)

---

說快不快，這樣就完成了 ComfyUI 的安裝與使用流程。希望這份教學對你有幫助，祝你玩得開心，創作愉快！

![第一張AI圖](https://res.cloudinary.com/dev7ziixx/image/upload/v1735550417/%E7%AC%AC%E4%B8%80%E5%BC%B5AI%E5%9C%96_zma3jh.png)