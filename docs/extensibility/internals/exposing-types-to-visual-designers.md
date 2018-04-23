---
title: 若要公開的視覺化設計工具的類型 |Microsoft 文件
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
ms.openlocfilehash: 28dcc17c74a5b5ef3c9784fafe972beb6f170d90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-types-to-visual-designers"></a>若要公開的視覺化設計工具的類型
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須能夠存取類別和類型定義在設計階段才能顯示視覺化設計工具。 類別會從一組預先定義的包含目前的專案 （參考加上其相依性） 的一組完整的相依性的組件載入。 它也可能需要的視覺化設計工具存取類別和自訂的工具所產生的檔案中定義的型別。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案系統支援透過暫存可攜式存取產生的類別和類型的可執行檔 (暫存 PEs)。 自訂工具產生的任何檔案可以編譯至暫存組件，能夠從這些組件載入及公開給設計工具類型。 每個自訂工具的輸出會先編譯成個別的 temporary PE，並成功或失敗的此暫存編譯僅取決於可以編譯所產生的檔案。 即使整個，可能無法建置專案，個別暫存 PEs 可能仍是提供給設計工具。  
  
 專案系統會提供完整支援變更追蹤輸出檔的自訂工具，前提是這些變更將會執行自訂工具的結果。 每次執行自訂工具時，會產生新的 temporary PE，並適當的通知傳送給設計工具。  
  
> [!NOTE]
>  臨時程式可執行檔的產生的檔案會在幕後，因為任何錯誤會不報告給使用者，如果編譯會失敗。  
  
 善用暫時的 PE 支援的自訂工具必須遵循下列規則：  
  
-   `GeneratesDesignTimeSource` 必須設定為 1 的登錄中。  
  
     沒有程式可執行檔編譯發生未進行此設定。  
  
-   產生的程式碼必須在相同的通用專案設定的語言。  
  
     無論做為要求的擴充功能中報告的自訂工具編譯 temporary PE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>前提`GeneratesDesignTimeSource`登錄中設定為 1。 擴充功能不需要是.vb、.cs 或.jsl;它可以是任何擴充功能。  
  
-   自訂工具產生的程式碼必須是有效的和它必須編譯時間在它自己使用只有參考專案中有一組<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>執行完成。  
  
     Temporary PE 編譯時，只提供給編譯器的原始程式檔時自訂工具輸出。 因此，使用 temporary PE 的自訂工具必須產生可以獨立於其他檔案專案中編譯的輸出檔。  
  
## <a name="see-also"></a>另請參閱  
 [BuildManager 物件簡介](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)