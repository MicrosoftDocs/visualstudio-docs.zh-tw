---
title: "自訂工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7589c9a2aedf987af79689e8babccb554fbb4ccc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tools"></a>自訂工具
*自訂工具*可讓您將工具與專案中的項目產生關聯，並執行該工具，每次您儲存檔案。 某些自訂的工具，有時也稱為*單一檔案產生器*，常用來實作轉譯器產生程式碼的資料，反之亦然。 例如，單一檔案產生器建立[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]超出.settings 和.resx 檔的原始程式碼。 產生的原始程式碼存取強型別.settings 和.resx 檔案中的資料。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型支援的自訂工具。[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案類型不這麼做。 您自己的專案類型也可以支援的自訂工具。  
  
 自訂工具是已註冊的元件，可實作`IVsSingleFileGenerator`介面。  
  
 自訂工具相關聯`ProjectItem`介面的物件，並就像設計工具和編輯器。 自訂工具會採用所表示的檔案`ProjectItem`做為輸入，並將寫入新的檔案其檔案名稱由`DefaultExtension`方法。  
  
## <a name="in-this-section"></a>本節內容  
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)  
 描述如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面，以實作自訂的工具。  
  
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)  
 提供的自訂工具的所有登錄項目說明。  
  
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 說明如何專案系統提供的支援存取產生的類別和類型的視覺化設計工具透過暫存的可攜式執行檔 (PE) 檔。  
  
 [保存專案項目的屬性](../../extensibility/persisting-the-property-of-a-project-item.md)  
 示範如何保存專案項目屬性，例如來源檔案，在專案檔中的作者。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 提供有關的詳細資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>，這會將單一輸入的檔案轉換成可以編譯，或加入至專案的單一輸出檔案。  
  
 <xref:EnvDTE.ProjectItem>  
 說明`ProjectItem`介面，代表專案中的項目。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 提供有關的詳細資料`DefaultExtension`方法，擷取指定的輸出檔案名稱的副檔名。  
  
## <a name="related-sections"></a>相關章節  
 [擴充專案](../../extensibility/extending-projects.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。