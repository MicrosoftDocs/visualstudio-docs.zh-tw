---
title: "如何：設定 IDE 協助工具選項 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: e55dee12df295fe794cad089a84897e36a90a1c8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-set-ide-accessibility-options"></a>如何：設定 IDE 協助工具選項
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包含功能，可讓視力障礙人士更容易閱讀，讓靈活度有限的人士更容易書寫。 這些功能包括在編輯器中變更文字的大小和色彩、變更工具列上的文字和按鈕大小，和自動完成方法及參數等等。  
  
 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援 Dvorak 鍵盤配置，這會讓最常鍵入的字元更容易存取。 您也可以自訂 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供的預設快速鍵。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="editors-dialogs-and-tool-windows"></a>編輯器、對話方塊和工具視窗  
 根據預設，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中的對話方塊和工具視窗使用與作業系統相同的字型大小和色彩。 IDE 框架、對話方塊、工具列和工具視窗的色彩設定，是以色彩配置為基礎：淡或暗。 您可以在[一般、環境、選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md)變更目前的色彩佈景主題。  
  
 您也可以在編輯器的 [程式碼] 檢視中顯示快顯視窗。 這些視窗可以提示您目前物件上的可用成員和參數，以便完成函式或陳述式。 如果您不方便鍵入，這些視窗會很有用。 不過，它們會干擾程式碼編輯器中的焦點，可能會對某些使用者造成問題。 您可以關閉這些視窗，方法是開啟 [選項] 對話方塊，並在 [選項] 對話方塊的 [文字編輯器]、[所有語言]、[一般] 頁面中，清除 [自動列出成員] 和 [參數資訊]。 如需詳細資訊，請參閱[如何：設定一般編輯器選項](http://msdn.microsoft.com/en-us/704e4a7b-2162-4bed-8a47-f4f6ffec98c2)。  
  
 您可以在整合式開發環境 (IDE) 中重新排列視窗，以符合您的工作方式。 您可以停駐、浮動、隱藏或自動隱藏每個工具視窗。  
  
 如需如何變更視窗配置的詳細資訊，請參閱[自訂視窗配置](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
### <a name="changing-the-size-of-text"></a>變更文字大小  
 您可以為以文字為基礎的工具視窗變更設定，例如 [命令] 視窗、[即時運算] 視窗，和 [輸出] 視窗，請使用 [工具] 對話方塊的 [環境] 選項中的 [字型和色彩] 窗格。 在 [顯示設定] 下拉式清單中選取 [所有文字工具視窗] 時，預設值會列為 [項目前景] 和 [項目背景] 下拉式清單中的 [預設]。 您也可以在編輯器中變更文字顯示方式的設定。  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>變更以文字為基礎的工具視窗和編輯器中的文字大小  
  
1.  從 [工具]  功能表選擇 [選項] 。  
  
2.  在 [環境] 資料夾上選擇 [字型和色彩]。  
  
3.  在 [顯示設定] 下拉式功能表上選取選項。  
  
     若要變更編輯器中文字的字型大小，請選擇 [文字編輯器]。  
  
     若要變更以文字為基礎之工具視窗中的文字字型大小，請選擇 [所有文字工具視窗]。  
  
     若要變更編輯器中工具提示文字的字型大小，請選擇 [編輯器工具提示]。  
  
     若要變更陳述式完成快顯視窗中文字的字型大小，請選擇 [陳述式完成]。  
  
4.  從 [顯示項目]，選取 [純文字]。  
  
5.  在 [字型] 中，選取新的字型類型。  
  
6.  在 [大小] 中，選取新的字型大小。  
  
    > [!NOTE]
    >  若要重設以文字為基礎之工具視窗和編輯器的文字大小，請選擇 [使用預設值]。  
  
7.  選擇 [ **確定**]。  
  
### <a name="changing-the-colors-used-in-the-ide"></a>變更 IDE 中使用的色彩  
 您也可以選擇變更編輯器中文字、邊界指標、空白字元和程式碼項目的預設色彩。  
  
> [!NOTE]
>  若要對您作業系統上的所有應用程式視窗使用高對比的色彩，請按左 **ALT+**左 **SHIFT+PRINT SCREEN**。 如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 已開啟，請關閉並重新開啟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，完整實作高對比色彩。  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>變更編輯器中項目的色彩  
  
1.  從 [工具]  功能表選擇 [選項] 。  
  
2.  從 [環境] 資料夾選擇 [字型和色彩]。  
  
3.  在 [顯示設定] 中，選擇 [文字編輯器]。  
  
4.  從 [顯示項目]，選取您要變更其顯示的項目，例如 [純文字]、[指示區邊界]、[可見的空白字元]、[HTML 屬性名稱] 或 [XML 屬性]。  
  
5.  從下列選項選取顯示設定：[項目前景]、[項目背景] 和 [粗體]。  
  
6.  選擇 [ **確定**]。  
  
## <a name="toolbars"></a>工具列  
 若要改善工具列的可用性和協助工具，您可以為工具列按鈕新增文字。  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>將文字指派給工具列按鈕  
  
1.  從 [工具] 功能表選擇 [自訂]。  
  
2.  在 [自訂] 對話方塊中，選取 [命令] 索引標籤。  
  
3.  選取 [工具列]，然後選擇包含您想要顯示文字之按鈕的工具列名稱。  
  
4.  在清單中，選取您想要變更的命令。  
  
5.  選擇 [修改選取項目]。  
  
6.  選擇 [影像和文字]。  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>修改按鈕的顯示文字  
  
1.  重新選取 [修改選取項目]。  
  
2.  在相鄰 [名稱] 處，提供選取按鈕的新標題。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 的協助工具功能](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [設計可及性應用程式的資源](../../ide/reference/resources-for-designing-accessible-applications.md)
