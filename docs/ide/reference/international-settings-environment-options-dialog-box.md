---
title: "選項對話方塊、環境、國際設定 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
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
ms.openlocfilehash: b92985ecd674fe750504c3aa85634b8c09fcdd5a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="international-settings-environment-options-dialog-box"></a>選項對話方塊、環境、國際設定
當您在電腦上安裝多個語言版本的整合式開發環境 (IDE) 時，[國際設定] 頁面可讓您變更預設語言。 您可以從 [工具] 功能表選取 [選項]，然後從 [環境] 資料夾選擇 [國際設定]，來存取這個對話方塊。 如果此頁面未出現在清單中，請在 [選項] 對話方塊中選取 [顯示所有設定]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
 **語言**  
 列出已安裝產品語言版本的可用語言。 除非您在電腦上安裝多個語言版本，否則無法使用這個選項。 如果產品的多個語言或產品的混合語言安裝共用環境，這個 [語言] 區段會變更為 [與 Microsoft Windows 相同]。  
  
> [!CAUTION]
>  在安裝了多個語言的系統中，Visual C++ 建置工具 (cl.exe、link.exe、nmake.exe、bscmake.exe 和相關檔案) 不會受到這項設定的影響。 由於 Visual C++ 建置工具不會使用附屬 DLL 模型，因此這些工具會使用最後一個安裝的語言版本，而且之前安裝的語言版本工具會遭到覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [安裝語言套件](../../install/install-visual-studio.md#install-language-packs)   
 [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)
