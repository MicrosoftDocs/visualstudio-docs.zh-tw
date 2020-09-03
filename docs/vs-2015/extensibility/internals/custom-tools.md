---
title: 自訂工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196923"
---
# <a name="custom-tools"></a>自訂工具
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*自訂工具* 可讓您將工具與專案中的專案建立關聯，並在儲存檔案時執行該工具。 某些自訂工具有時稱為 *單一*檔案產生器，經常用來執行從資料產生程式碼的轉譯程式，反之亦然。 例如，單一檔案產生器會 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 從設定和 .resx 檔建立和原始程式碼。 產生的原始程式碼會提供對. 設定和 .resx 檔中資料的強型別存取。 [!INCLUDE[csprcs](../../includes/csprcs-md.md)]和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案類型支援自訂工具， [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案類型則不支援。 您自己的專案類型也可以支援自訂工具。  
  
 自訂工具是用來執行介面的註冊元件 `IVsSingleFileGenerator` 。  
  
 自訂工具會與 `ProjectItem` 介面物件相關聯，而且類似于設計工具和編輯器。 自訂工具會採用以 `ProjectItem` 做為輸入的檔案，並寫入新檔案，該檔案的檔案名是由 `DefaultExtension` 方法所提供。  
  
## <a name="in-this-section"></a>本節內容  
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)  
 描述如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 介面來執行自訂工具。  
  
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)  
 說明如何根據所使用的語言判斷正確的命名空間。  
  
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)  
 提供自訂工具所有登錄專案的描述。  
  
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 說明專案系統如何提供視覺化設計工具支援，透過暫時性可執行檔 (PE) 檔來存取產生的類別和類型。  
  
 [保存專案項目的屬性](../../extensibility/persisting-the-property-of-a-project-item.md)  
 顯示如何在專案檔中保存專案專案屬性，例如原始程式檔的作者。  
  
## <a name="reference"></a>參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 提供的詳細資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> ，它會將單一輸入檔轉換成單一輸出檔案，該檔案可以編譯或新增至專案。  
  
 <xref:EnvDTE.ProjectItem>  
 說明 `ProjectItem` 代表專案中專案的介面。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 提供方法的詳細資料 `DefaultExtension` ，該方法會抓取提供給輸出檔名稱的副檔名。  
  
## <a name="related-sections"></a>相關章節  
 [擴充專案](../../extensibility/extending-projects.md)  
 描述如何使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。
