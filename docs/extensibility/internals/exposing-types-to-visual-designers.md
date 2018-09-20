---
title: 將類型公開至視覺化設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f1820b3df61dd8029ac9404eb7f4a09e44707ac
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370623"
---
# <a name="expose-types-to-visual-designers"></a>公開至視覺化設計工具的型別
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須能夠存取類別和類型定義在設計階段才能顯示視覺化設計工具。 類別會從一組預先定義的包含目前的專案 （參考，加上其相依性） 的完整相依性集合的組件載入。 它也可能需要的視覺化設計工具存取類別和自訂工具所產生的檔案中定義的類型。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案系統會提供支援透過暫存可攜式存取產生的類別和類型的可執行檔 (暫存 PEs)。 自訂工具產生的任何檔案可以編譯成暫存組件，如此才能從這些組件載入並且公開至設計工具型別。 每個自訂工具的輸出會編譯成個別的 temporary PE，並成功或失敗的這個暫存編譯僅取決於可以編譯所產生的檔案。 即使整個，可能無法建置專案，個別的暫存 PEs 可能仍然可以設計工具。  
  
 專案系統的變更追蹤輸出檔的自訂工具，提供完整支援，前提是這些變更是執行自訂工具的結果。 每次執行自訂工具時，會產生新的 temporary PE，並適當的通知傳送給設計工具。  
  
> [!NOTE]
>  臨時程式可執行檔的產生檔案會在背景執行，因為沒有任何錯誤會回報給使用者，如果編譯失敗。  
  
 利用暫時的 PE 支援的自訂工具必須遵循下列規則：  
  
-   **GeneratesDesignTimeSource**必須在登錄中設定為 1。  
  
     不程式可執行檔會進行編譯而不需要這項設定。  
  
-   產生的程式碼必須位於相同的通用專案設定的語言。  
  
     不論什麼自訂工具會回報為要求的擴充功能，在編譯 temporary PE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>前提**GeneratesDesignTimeSource**在登錄中設定為 1。 延伸模組不一定要 *.vb*， *.cs*，或 *.jsl*; 它可以是任何擴充功能。  
  
-   自訂工具產生的程式碼必須有效，且它必須編譯時間在它自己使用只存在於專案中參考的組<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>完成執行。  
  
     Temporary PE 編譯時，只提供給編譯器的原始程式檔就會是自訂工具輸出。 因此，使用暫存的 PE 的自訂工具必須產生可以獨立於其他檔案專案中編譯的輸出檔。  
  
## <a name="see-also"></a>另請參閱  
 [BuildManager 物件簡介](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)