---
title: "自訂 Visual Studio 如何建立資料繫結控制項的標題 |Microsoft 文件"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 86f0e451fe81875868db0d6ddcd9cead790800d3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自訂 Visual Studio 如何建立資料繫結控制項的標題
當您拖曳項目從[資料來源視窗](add-new-data-sources.md)拖曳至設計工具中，特殊的考量派上用場： 標題標籤資料行名稱重新格式化成更容易讀取的字串當兩個或多個單字所找到不串連在一起。 您可以自訂建立的方式，這些標籤，藉由設定**SmartCaptionExpression**， **SmartCaptionReplacement**，和**SmartCaptionSuffix**中的值**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data 設計工具**登錄機碼。  
  
> [!NOTE]
> 此登錄機碼不存在，您必須建立它。  
  
智慧標題由輸入的值的規則運算式**SmartCaptionExpression**值。 加入**資料設計工具**登錄機碼會覆寫的預設規則運算式，控制標題標籤。 如需有關規則運算式的詳細資訊，請參閱[使用 Visual Studio 中的規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
下表描述控制標題標籤的登錄值。  
  
|登錄項目|說明|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|用來比對模式的規則運算式。|  
|**SmartCaptionReplacement**|若要顯示在比對任何群組的格式**SmartCaptionExpression**。|  
|**SmartCaptionSuffix**|要附加至標題結尾的選擇性字串。|  
  
下表列出這些登錄值的內部預設值。  
  
|登錄項目|預設值|說明|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124; _ +|比對後面接著大寫的字元或底線小寫字元。|  
|**SmartCaptionReplacement**|$1 $2|$1 代表中第一個運算式的括號比對任何字元，而 $2 代表第二個括號中比對任何字元。 取代為第一個相符項目、 一個空格，然後第二個相符項目。|  
|**SmartCaptionSuffix**|:|表示附加至傳回之字串的字元。 例如，如果標題為`Company Name`後, 置詞可讓`Company Name:`|  
  
> [!CAUTION]
> 您必須非常小心，進行設定時在 登錄編輯器。 編輯前先備份登錄。 如果您不當使用登錄編輯程式，您可以會導致嚴重的問題，可能需要重新安裝作業系統。 Microsoft 不保證可解決您不當使用登錄編輯程式而造成的問題。 您必須自行承擔使用登錄編輯器的風險。  
>   
>  下列知識庫文件包含備份、 編輯和還原登錄的指示： [Microsoft Windows 登錄說明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)（（英文)256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>若要修改智慧的隱藏式字幕功能行為的資料來源視窗  
  
1.  開啟命令視窗中，依序按一下**啟動**然後**執行**。  
  
2.  型別`regedit`中**執行**對話方塊中，然後按一下**確定**。  
  
3.  展開**HKEY_CURRENT_USER**，**軟體*， **Microsoft**， **VisualStudio**節點。  
  
7.  以滑鼠右鍵按一下**15.0**  節點，並建立新**金鑰**名為`Data Designers`。  
  
8.  以滑鼠右鍵按一下**資料設計工具** 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 以滑鼠右鍵按一下**SmartCaptionExpression**值，並選取**修改**。  
  
12. 輸入您想要的規則運算式**資料來源**視窗即可使用。  
  
13. 以滑鼠右鍵按一下**SmartCaptionReplacement**值，並選取**修改**。  
  
14. 輸入要取代的字串格式的方式，您想要顯示在您的規則運算式中比對的模式。  
  
15. 以滑鼠右鍵按一下**SmartCaptionSuffix**值，並選取**修改**。  
  
16. 輸入您想要顯示的標題結尾的任何字元。  
  
    下次您拖曳項目，從**資料來源**視窗中，建立標題標籤使用提供的新登錄值。  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>若要關閉智慧的隱藏式字幕功能  
  
1.  開啟命令視窗中，依序按一下**啟動**然後**執行**。  
  
2.  型別`regedit`中**執行**對話方塊中，然後按一下**確定**。  
  
3.  展開**HKEY_CURRENT_USER**，**軟體**， **Microsoft**， **VisualStudio**節點。  
  
7.  以滑鼠右鍵按一下**15.0**  節點，並建立新**金鑰**名為`Data Designers`。  
  
8.  以滑鼠右鍵按一下**資料設計工具** 節點，並建立三個新的字串值：

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 以滑鼠右鍵按一下**SmartCaptionExpression**項目，然後選取**修改**。  
  
12. 輸入`(.*)`值。 這會比對整個字串。  
  
13. 以滑鼠右鍵按一下**SmartCaptionReplacement**項目，然後選取**修改**。  
  
14. 輸入`$1`值。 這會將字串取代相符的值，也就是整個字串，以便將維持不變。  
  
    下次您拖曳項目，從**資料來源**視窗中，與未修改的標題，會建立標題標籤。  
  
## <a name="see-also"></a>另請參閱  
[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)