# 第一次的 Flux 探索之旅

在 AI 圖片生成的世界裡，各式各樣的模型層出不窮。選擇哪個模型，不僅關乎效果，更取決於它的未來發展潛力。手邊只有一張 3070 顯示卡的情況下，我最終選擇了由 **Black Forest Labs** 開發的 **Flux**，一款兼具性能與未來性的模型。

你可能會問，為什麼我一直提到「時間」？因為 AI 的進步速度實在快得驚人。就在 2025 年初，Flux 是我認為的最佳選擇，但可能一年後就會有全新工具取而代之。所以，如果你對這些技術感興趣，建議現在就動手嘗試，因為 AI 的每一次進步，都值得我們搶先體驗！

![Flux1_schnell 第二次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823193/Flux1_schnell%E7%AC%AC%E4%BA%8C%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_ckdysm.png)

### **Flux1 模組簡介與安裝**

Flux1 提供了三個不同的 checkpoint，它們分別有不同的介紹：
- **`flux1_pro`**：收費，有最高品質的圖片生成能力。
- **`flux1_dev`**：開源免費，主要提供個人實驗性功能，不可商用。
- **`flux1_schnell`**：開源免費，圖片生成能力據說較弱，但速度較快，可商用。
  
![Flux1 版本比較](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808083/Flux1%E7%89%88%E6%9C%AC%E6%AF%94%E8%BC%83_brdkck.png)

在第一次接觸FLux1的情況下，我將著重在使用`flux1_dev`與`flux1_schnell`。

## **FLux1 下載與安裝**

關於Flux1 的下載與安裝，我主要參考下列兩個網頁，是ComfyUI如何安裝Flux1的説明，兩個頁面的檔案放置路徑有點出入，我會將我放的位置提供給大家。
裡面有提到好幾種安裝的方式，原因是因為Flux1官方版本的使用上比較複雜，所以會有一些經過處理的，較為輕量或是比較方便使用的版本，這次會介紹的是：
1.Black forest labs，也就是官方提供的model。
2.ComfyUI提供的方便使用版本。

[ComfyUI Wiki Flux1 範例](https://comfyui-wiki.com/zh/tutorial/advanced/flux1-comfyui-guide-workflow-and-examples)

![ComfyUI Wiki Flux1 範例](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808376/ComfyUI_Wiki_Flux1%E7%AF%84%E4%BE%8B_yw2oaj.png)

[ComfyUI Flux1 範例](https://comfyanonymous.github.io/ComfyUI_examples/flux/)

![ComfyUI Flux1 範例](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808451/ComfyUI_Flux1%E7%AF%84%E4%BE%8B_a9xmpo.png)

---

## **Black forest labs FLux1**

### **檔案下載**
首先下載需要的所有檔案

| 檔案                         | 下載連結                                                                                                                         | 擺放位置                         |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| clip_l.safetensors           | [Clip From Huggingface](https://huggingface.co/comfyanonymous/flux_text_encoders/blob/main/clip_l.safetensors)                   | ComfyUI/models/clip/             |
| t5xxl_fp16.safetensors       | [Text Encoder From Huggingface](https://huggingface.co/comfyanonymous/flux_text_encoders/blob/main/t5xxl_fp16.safetensors)       | ComfyUI/models/text_encoders/    |
| t5xxl_fp8_e4m3fn.safetensors | [Text Encoder From Huggingface](https://huggingface.co/comfyanonymous/flux_text_encoders/blob/main/t5xxl_fp8_e4m3fn.safetensors) | ComfyUI/models/text_encoders/    |
| ae.safetensors               | [VAE From Huggingface](https://huggingface.co/black-forest-labs/FLUX.1-schnell/blob/main/ae.safetensors)                         | ComfyUI/models/vae/              |
| flux1-dev.safetensors        | [Model From Huggingface](https://huggingface.co/black-forest-labs/FLUX.1-dev/blob/main/flux1-dev.safetensors)                    | ComfyUI/models/diffusion_models/ |
| flux1-schnell.safetensors    | [Model From Huggingface](https://huggingface.co/black-forest-labs/FLUX.1-schnell/blob/main/flux1-schnell.safetensors)            | ComfyUI/models/unet/             |

### **Flux1 範例 Workflow**

ComfyUI 的官方 Wiki 提供了 Flux1 的範例 Workflow 配置：[Flux官方範例與說明](https://comfyui-wiki.com/zh/tutorial/advanced/flux1-comfyui-guide-workflow-and-examples)

**Flux1_dev 範例 Workflow**  
Flux-Dev-ComfyUI-Workflow.json

![Flux1_dev 範例 Workflow](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808733/Flux1_dev%E7%AF%84%E4%BE%8BWorkflow_dd8byh.png)

**Flux1_schnell 範例 Workflow**  
Flux-Schnell-ComfyUI-Workflow.json

![Flux1_schnell 範例 Workflow](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808911/Flux1_schnell%E7%AF%84%E4%BE%8BWorkflow_qwdead.png)

### **運行 Flux1 Workflow**

#### **運行 Flux1_dev**
運行 Flux1_dev 的範例 Workflow，生成了如下的成果圖片：

![Flux1_dev 成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735822717/Flux1_dev%E6%88%90%E6%9E%9C_ggfabz.png)

在這個workflow中的seed，也就是種子碼，用在決定程序中的隨機數值，設定為運行後任意隨機一次，所以我們可以在運行一次看看其他不同的結果。

![Flux1_dev 第二次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735822770/Flux1_dev%E7%AC%AC%E4%BA%8C%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_vjokmh.png)

#### *運行 Flux1_schnell**
接著，我運行了 Flux1_schnell 的範例 Workflow，並生成了一組圖片：

![Flux1_schnell 成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823194/Flux1_schnell%E6%88%90%E6%9E%9C_yseovg.png)

同樣再次運行一次看看其他不同的結果。

![Flux1_schnell 第二次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823193/Flux1_schnell%E7%AC%AC%E4%BA%8C%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_ckdysm.png)

---

## **ComfyUI FLux1**

### **檔案下載**
首先下載需要的所有檔案

| 檔案                      | 下載連結                                                                                                              | 擺放位置                    |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| flux1-dev-fp8.safetensors | [Checkpoint From Huggingface](https://huggingface.co/Comfy-Org/flux1-dev/blob/main/flux1-dev-fp8.safetensors)         | ComfyUI/models/checkpoints/ |
| flux1-schnell.safetensors | [Checkpoint From Huggingface](https://huggingface.co/Comfy-Org/flux1-schnell/blob/main/flux1-schnell-fp8.safetensors) | ComfyUI/models/checkpoints/ |

### **ComfyUI Flux1 範例 Workflow**

ComfyUI 的官方 Wiki 同樣有提供了 ComfyUI Flux1 的範例 Workflow 配置：[Flux官方範例與說明](https://comfyui-wiki.com/zh/tutorial/advanced/flux1-comfyui-guide-workflow-and-examples)

**Flux1_dev 範例 Workflow**  
flux_dev_checkpoint_example.json

![ComfyUI Flux1_dev 範例 Workflow](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808732/ComfyUI_Flux1_dev%E7%AF%84%E4%BE%8BWorkflow.png_wvuwxc.png)

**Flux1_schnell 範例 Workflow**  
flux_schnell_checkpoint_example.json

![ComfyUI Flux1_schnell 範例 Workflow](https://res.cloudinary.com/dev7ziixx/image/upload/v1735808910/ComfyUI_Flux1_schnell%E7%AF%84%E4%BE%8BWorkflow_habx7b.png)

### **運行 ComfyUI Flux1 Workflow**

#### **運行 ComfyUI Flux1_dev**
運行 Flux1_dev 的範例 Workflow，生成了如下的成果圖片，果然與範例圖片一模一樣：

![ComfyUI Flux1_dev 成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823531/ComfyUI_Flux1_dev%E6%88%90%E6%9E%9C_a44lcr.png)

同樣再次運行一次看看其他不同的結果。

![ComfyUI Flux1_dev 第二次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823529/ComfyUI_Flux1_dev%E7%AC%AC%E4%BA%8C%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_p1unk3.png)


#### *運行 ComfyUI Flux1_schnell**
接著，我運行了 Flux1_schnell 的範例 Workflow，並生成了一組圖片：

![ComfyUI Flux1_schnell 成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823636/ComfyUI_Flux1_schnell%E6%88%90%E6%9E%9C_kxg0zz.png)

同樣再次運行一次看看其他不同的結果。

![ComfyUI Flux1_schnell 第二次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823638/ComfyUI_Flux1_schnell%E7%AC%AC%E4%BA%8C%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_wrcemm.png)

---

接下來，我將會深入研究如何進一步自定義 Flux 的 Workflow，並嘗試結合其他工具，創建出更具個性化與創意的 AI 圖片作品。

期待未來能和大家分享更多探索過程中的有趣發現！如果你對 Flux 有任何想法或心得，也歡迎一起討論！

![Flux1_schnell 第三次運行成果](https://res.cloudinary.com/dev7ziixx/image/upload/v1735823352/Flux1_schnell%E7%AC%AC%E4%B8%89%E6%AC%A1%E9%81%8B%E8%A1%8C%E6%88%90%E6%9E%9C_qsrtlu.png)

---

參考資料：

[ComfyUI Wiki ： https://comfyui-wiki.com](https://comfyui-wiki.com/zh/tutorial/advanced/flux1-comfyui-guide-workflow-and-examples)


[ComfyUI Flux1 Example : https://comfyanonymous.github.io/ComfyUI_examples/flux/](https://comfyanonymous.github.io/ComfyUI_examples/flux/)