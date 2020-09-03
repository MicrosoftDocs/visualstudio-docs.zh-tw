---
title: 將類型公開至視覺化設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691196"
---
# <a name="exposing-types-to-visual-designers"></a>將類型公開至視覺化設計工具
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 必須能夠在設計階段存取類別和類型定義，才能顯示視覺化設計工具。 類別是從一組預先定義的元件載入，其中包含目前專案的完整相依性集合， (參考加上) 的相依性。 視覺化設計工具也可能需要存取自訂工具所產生的檔案中所定義的類別和類型。  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]和 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 專案系統透過暫存的可執行檔 (暫時性的 pe) ，支援存取產生的類別和類型。 自訂工具產生的任何檔案都可以編譯成暫存元件，以便從這些元件載入型別並公開給設計工具。 每個自訂工具的輸出會編譯成個別的暫存 PE，而此暫存編譯的成功或失敗只取決於是否可以編譯產生的檔案。 雖然專案可能不會以整體方式建立，但設計工具還是可以使用個別的暫存 Pe。  
  
 專案系統提供完整的支援，可追蹤自訂工具輸出檔的變更，但前提是這些變更是執行自訂工具的結果。 每次執行自訂工具時，都會產生新的暫存 PE，並將適當的通知傳送至設計工具。  
  
> [!NOTE]
> 因為暫時性程式可執行檔產生檔會在背景中執行，所以如果編譯失敗，就不會向使用者回報錯誤。  
  
 利用暫時性 PE 支援的自訂工具必須遵循下列規則：  
  
- `GeneratesDesignTimeSource` 必須在登錄中設定為1。  
  
     沒有此設定，就不會進行程式可執行檔編譯。  
  
- 產生的程式碼必須與全域專案設定的語言相同。  
  
     無論自訂工具是在登錄中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> `GeneratesDesignTimeSource` 設定為1時所提供的要求延伸模組為何，都會編譯暫存 PE。 延伸模組不需要是 .vb、.cs 或. form1.jsl;它可以是任何延伸模組。  
  
- 自訂工具產生的程式碼必須是有效的，而且它必須只使用在執行完成時存在於專案中的一組參考來進行編譯 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 。  
  
     編譯暫存 PE 時，唯一提供給編譯器的原始程式檔是自訂工具輸出。 因此，使用暫存 PE 的自訂工具必須產生輸出檔案，而這些輸出檔案可以獨立于專案中的其他檔案進行編譯。  
  
## <a name="see-also"></a>另請參閱  
 [BuildManager 物件簡介](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [執行單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)
