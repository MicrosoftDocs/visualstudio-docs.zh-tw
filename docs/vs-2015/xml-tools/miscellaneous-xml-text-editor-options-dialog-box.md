---
title: 其他、 XML、 文字編輯器、 選項對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: edf638420ac41d6ad6f7ebf5e20ab5d78d1c7b3d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435362"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>其他、XML、文字編輯器、選項對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此對話方塊可讓您變更 XML 編輯器的自動完成及結構描述設定。 您可以存取**選項**對話方塊中，從**工具**功能表。  
  
> [!NOTE]
> 這些設定都是當您選取**文字編輯器**資料夾中， **XML**資料夾，然後**其他**選項**選項**  對話方塊。  
  
## <a name="auto-insert"></a>自動插入  
 **結尾標記**  
 如果已核取 自動完成設定，編輯器在您鍵入右角括弧 (>)，以關閉開始標記時，如果標記尚未關閉時自動加入結束標記。 這是預設行為。  
  
 空白項目的完成不會依賴自動完成設定。 您可以隨時輸入反斜線 (/) 以自動完成空白項目。  
  
 **屬性引號**  
 撰寫 XML 屬性時，編輯器會插入 `=" "` 字元，並將插入號 (^) 置於雙引號內。  
  
 預設會選取。  
  
 **命名空間宣告**  
 編輯器會自動在需要的位置插入命名空間宣告。  
  
 預設會選取。  
  
 **其他標記 (註解、CDATA)**  
 會自動完成註解、CDATA、DOCTYPE、處理指示及其他標記。  
  
 預設會選取。  
  
## <a name="network"></a>網路  
 **自動下載 DTD 及結構描述**  
 自動從 HTTP 位置下載結構描述及文件類型定義 (DTD)。 此功能會使用已啟用自動 Proxy 伺服器偵測的 System.Net。  
  
 預設會選取。  
  
## <a name="outlining"></a>大綱  
 **檔案開啟時進入大綱模式**  
 會在檔案開始時開啟大綱功能。  
  
 預設會選取。  
  
## <a name="caching"></a>快取  
 **結構描述**  
 指定結構描述快取的位置。 瀏覽按鈕 (**...**) 開啟**目錄瀏覽**對話方塊在目前的結構描述快取位置。 您可以選取不同的目錄，或您可以在對話方塊中，選取的資料夾按一下滑鼠右鍵，然後選擇**開啟**看到目錄中的項目。  
  
## <a name="see-also"></a>另請參閱  
 [屬性視窗、 XML 文件屬性](../xml-tools/xml-document-properties-properties-window.md)   
 [XML 編輯器元件](../xml-tools/xml-editor-components.md)
