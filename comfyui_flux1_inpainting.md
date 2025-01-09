# **補上 AI 圖片的每一筆細節**  

在生成 AI 圖片的過程中，我們常常會遇到圖片某些部分細節不足、缺失甚至出錯的情況。這時，**Inpainting（局部修補）** 技術就派上用場了！這篇文章將帶你一步步了解如何利用 **Flux** 和 **ComfyUI** 來修補圖片細節，讓你的 AI 圖片更加精緻完美。

![Inpainting 第二種結果](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388127/Inpainting_%E7%AC%AC%E4%BA%8C%E7%A8%AE%E7%B5%90%E6%9E%9C_ptxyfw.png)  
   
---

## **什麼是 Inpainting？為什麼重要？**  

Inpainting 是 AI 圖像生成中用來針對圖片特定區域進行修補或重新生成的技術。它可以在保留圖片整體風格的同時，強化細節或修正缺陷。以下是幾個常見的應用場景：  
- **修復圖像缺失**：例如填補背景或物件的空白區域。  
- **優化局部細節**：增強人物的五官細節或服裝的紋理效果。  
- **調整風格和內容**：針對特定區域進行風格化改造，使整體圖片更和諧。  

Inpainting 是讓接近完成的圖片更上一層樓的關鍵工具。

---

## **準備工作：下載所需模組**  

首先，你需要準備 ComfyUI 支援的 Inpainting 模型。前往以下頁面下載相關檔案：  
[ComfyUI Flux1 inpainting](https://comfyanonymous.github.io/ComfyUI_examples/flux/)  
![ComfyUI Flux1 Inpainting範例](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388129/ComfyUI_Flux1_Iinpainting%E7%AF%84%E4%BE%8B_eep5vk.png)  

下載完成後，將檔案放置於以下路徑：  
```
ComfyUI/models/diffusion_models/
```  

該頁面還提供了範例 Workflow（工作流程），只需將範例檔案拖入 ComfyUI，即可快速開啟 Inpainting 的專用工作流程。  

![ComfyUI Inpainting Workflow](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388127/ComfyUI_Inpainting_Workflow_zgfp0k.png)

---

## **操作步驟：選取修復區域**  

**上傳圖片**  
   點擊 ComfyUI 的「Upload」按鈕，選擇要修復的圖片。 
   ![修正圖片](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388128/%E4%BF%AE%E6%AD%A3%E5%9C%96%E7%89%87_m8r0sr.png)  

**選擇修補區域**  
   右鍵圖片，選擇「Open in MaskEditor」來進行區域選取。  
   ![開啟區域選取](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388127/%E9%96%8B%E5%95%9F%E5%8D%80%E5%9F%9F%E9%81%B8%E5%8F%96_lzltm1.png)  

**畫出需要修補的區域**  
   使用滑鼠畫出需要修補的區域。  
   ![畫出區域](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388129/%E7%95%AB%E5%87%BA%E5%8D%80%E5%9F%9F_j0ozij.png)  

**保存區域選擇**  
   按下「Save」後，選取區域會顯示於圖片上。  
   ![完成區域選擇](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388127/%E5%AE%8C%E6%88%90%E5%8D%80%E5%9F%9F%E9%81%B8%E6%93%87_siz72g.png)  

---

## **執行區域修補**  

填入適合的 **Prompt（提示詞）**，描述你希望修補區域呈現的內容或風格。  
按下「Queue」，運行工作流程，完成修補操作。  
   ![Inpainting 結果](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388130/Inpainting_%E7%B5%90%E6%9E%9C_sx6e81.png)  

若修改提示詞內容跟區域，可以生成不同的修補效果：  
   ![Inpainting 第二種結果](https://res.cloudinary.com/dev7ziixx/image/upload/v1736388127/Inpainting_%E7%AC%AC%E4%BA%8C%E7%A8%AE%E7%B5%90%E6%9E%9C_ptxyfw.png)  

---

參考資料：  
- [ComfyUI Flux1 Example](https://comfyanonymous.github.io/ComfyUI_examples/flux/)  

---

希望這篇文章能幫助你更好地理解 Inpainting 技術並應用於你的 AI 圖片創作中！如果你有任何疑問或想法，歡迎在下方留言分享你的經驗！ 😊  
