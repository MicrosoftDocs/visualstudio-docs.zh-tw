---
title: HOW TO：儲存及開啟檔案以編碼方式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb4e07f90f3a05f61957898c579b9a70da6e5ce1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039223"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>HOW TO：儲存及開啟檔案以編碼方式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用特定的字元編碼來儲存檔案，以支援雙向語言。 您也可以在開啟檔案時指定編碼方式，讓 Visual Studio 正確顯示檔案。  
  
### <a name="to-save-a-file-with-encoding"></a>以編碼方式儲存檔案  
  
1. 從 [檔案] 功能表上，選擇 [另存新檔]，然後按一下 [儲存] 按鈕旁的下拉式按鈕。  
  
     [進階儲存選項] 對話方塊隨即顯示。  
  
2. 在 [編碼] 下方，選取檔案要使用的編碼方式。  
  
3. 您也可以在 [行尾結束符號] 下方，選取行結尾字元的格式。  
  
     如果您想要與不同作業系統的使用者交換檔案，這個選項相當實用。  
  
     如果您知道要使用的檔案是以何種方式編碼，即可在開啟檔案時告知 Visual Studio 使用該種編碼方式。 依據檔案是否為專案的一部分而定，您需使用不同的方法。  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>若要開啟的編碼檔案為專案的一部分  
  
1. 在方案總管中，以滑鼠右鍵按一下檔案，並選擇 [開啟方式]。  
  
2. 在 [開啟方式] 對話方塊中，選擇要開啟檔案的編輯器。  
  
     許多 Visual Studio 編輯器 (例如表單編輯器) 會自動偵測編碼，並以適當方式開啟檔案。 如果您選擇的編輯器可讓您選擇編碼方式，即會顯示 [編碼] 對話方塊。  
  
3. 在 [編碼] 對話方塊中，選取編輯器應該使用的編碼方式。  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>若要開啟的編碼檔案不是專案的一部分  
  
1. 在 [檔案] 功能表上，指向 [開啟]，並選擇 [檔案] 或 [從 Web 開啟檔案]，然後選取要開啟的檔案。  
  
2. 按一下 [開啟] 按鈕旁的下拉式按鈕，然後選擇 [開啟方式]。  
  
3. 遵循上述程序步驟 2 和 3。  
  
## <a name="see-also"></a>另請參閱  
 [編碼方式和 Windows Forms 全球化](http://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
