---
title: 自訂 Visual Studio 建立資料繫結控制項的標題的方式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf3d47c4e14606a4d3cc3006735fbe04af809600
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195607"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>自訂 Visual Studio 為資料繫結的控制項建立標題的方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
當您拖曳項目從[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至 Windows Form 設計工具中，特殊的考量派上用場： 標題標籤中的資料行名稱重新格式化成更容易閱讀的字串當兩個或更多的字找到要串連在一起。 您可以自訂這些標籤建立所在，藉由設定的方式**SmartCaptionExpression**， **SmartCaptionReplacement**，並**SmartCaptionSuffix**中的值**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data 設計工具**登錄機碼。  
  
> [!NOTE]
>  此登錄機碼不存在，您必須建立它。  
  
 智慧標題會受到輸入的值的規則運算式**SmartCaptionExpression**值。 新增**資料設計工具**登錄機碼會覆寫預設規則運算式，控制標題標籤。 如需有關規則運算式的詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
 下表描述控制項標題標籤的登錄值。  
  
|登錄項目|描述|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|用來比對模式的規則運算式。|  
|**SmartCaptionReplacement**|若要顯示在比對任何群組的格式**SmartCaptionExpression**。|  
|**SmartCaptionSuffix**|要附加至標題結尾選擇性的字串。|  
  
 下表列出這些登錄值的內部預設設定。  
  
|登錄項目|預設值|說明|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|比對後面接著大寫的字元或底線為小寫字元。|  
|**SmartCaptionReplacement**|$1 $2|$1 代表第一個運算式的括號中比對任何字元而 $2 代表第二個括號中比對任何字元。 取代為第一個相符項目、 一個空格，然後第二個相符項目。|  
|**SmartCaptionSuffix**|:|表示附加至傳回字串的字元。 例如，如果標題是`Company Name`後, 置詞可讓 `Company Name:`|  
  
> [!CAUTION]
>  您必須非常小心進行任何項目在 登錄編輯時。 編輯前先備份登錄。 如果您不當使用登錄編輯程式，您可以會造成嚴重的問題，可能會要求您重新安裝作業系統。 Microsoft 不保證您不當使用登錄編輯程式而造成的問題，可以解決。 您必須自行承擔使用登錄編輯器的風險。  
>   
>  下列知識庫文件包含針對備份、 編輯和還原登錄的指示： [Microsoft Windows 登錄說明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)(http://support.microsoft.com/default.aspx?scid=kb; en-us-我們; 256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>若要修改智慧的隱藏式字幕功能行為的資料來源 視窗  
  
1.  開啟命令視窗中，依序按一下**開始**，然後**執行**。  
  
2.  型別`regedit`中**執行** 對話方塊中，然後按一下**確定**。  
  
3.  依序展開**HKEY_CURRENT_USER**節點。  
  
4.  依序展開**軟體**節點。  
  
5.  依序展開**Microsoft**節點。  
  
6.  依序展開**VisualStudio**節點。  
  
7.  以滑鼠右鍵按一下**10.0**節點，並建立新**金鑰**名為`Data Designers`。  
  
8.  以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionExpression`。  
  
9. 以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionReplacement`。  
  
10. 以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionSuffix`。  
  
11. 以滑鼠右鍵按一下**SmartCaptionExpression**項目，然後選取**修改**。  
  
12. 輸入您想要的規則運算式**Zdroje dat**視窗，以使用。  
  
13. 以滑鼠右鍵按一下**SmartCaptionReplacement**項目，然後選取**修改**。  
  
14. 輸入要取代的字串格式化的方式，您想要顯示在您的規則運算式比對的模式。  
  
15. 以滑鼠右鍵按一下**SmartCaptionSuffix**項目，然後選取**修改**。  
  
16. 輸入任何您想要顯示的標題結尾的字元。  
  
     在下一次將項目從**Zdroje dat**  視窗中，建立標題標籤使用提供的新登錄值。  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>若要關閉智慧型的隱藏式輔助字幕功能  
  
1.  開啟命令視窗中，依序按一下**開始**，然後**執行**。  
  
2.  型別`regedit`中**執行** 對話方塊中，然後按一下**確定**。  
  
3.  依序展開**HKEY_CURRENT_USER**節點。  
  
4.  依序展開**軟體**節點。  
  
5.  依序展開**Microsoft**節點。  
  
6.  依序展開**VisualStudio**節點。  
  
7.  以滑鼠右鍵按一下**10.0**節點，並建立新**金鑰**名為`Data Designers`。  
  
8.  以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionExpression`。  
  
9. 以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionReplacement`。  
  
10. 以滑鼠右鍵按一下**資料設計工具**節點，並建立新**字串值**名為`SmartCaptionSuffix`。  
  
11. 以滑鼠右鍵按一下**SmartCaptionExpression**項目，然後選取**修改**。  
  
12. 輸入`(.*)`值。 這會比對整個字串。  
  
13. 以滑鼠右鍵按一下**SmartCaptionReplacement**項目，然後選取**修改**。  
  
14. 輸入`$1`值。 這會將字串取代相符的值，也就是整個字串，以便將維持不變。  
  
     在下一次將項目從**Zdroje dat**  視窗中，與未修改的標題，會建立標題標籤。  
  
## <a name="see-also"></a>另請參閱  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)

