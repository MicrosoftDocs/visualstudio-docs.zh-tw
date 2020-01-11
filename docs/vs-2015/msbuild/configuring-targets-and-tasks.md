---
title: 設定目標和工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 892e9615599a8881e219c00f748a0cc1567d996d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850037"
---
# <a name="configuring-targets-and-tasks"></a>設定目標和工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以設定 MSBuild 目標和工作以跨處理序方式隨 MSBuild 一起執行，如此您就能以與目前執行的內容不同的內容做為目標。 例如，您可以在開發電腦以 64 位元 .NET Framework 4.5 作業系統執行時，以 32 位元 .NET Framework 2.0 應用程式為目標。 您也可以將執行 .NET Framework 4 或以前版本的電腦做為目標。 32 或 64 位元與特定 .NET Framework 版本的組合稱為「目標內容」。  
  
## <a name="installation"></a>安裝  
 .NET Framework 4.5 和 4.5.1 會取代 .NET Framework 4 的通用語言執行平台 (CLR)、目標、工作和工具，而不會將它們重新命名。 .NET Framework 4.5.1 會安裝為 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 的一部分。  
  
 如果您想要將 MSBuild 與 Visual Studio 分開安裝，可以從 [MSBuild 下載](https://www.microsoft.com/download/details.aspx?id=40760)下載安裝套件。 另外，您必須安裝要同時使用的 .NET Framework 版本。  
  
## <a name="targets-and-tasks"></a>目標和工作  
 MSBuild 會以跨處理序的方式執行一些建置工作，以鎖定範圍更廣的內容。  例如，32 位元 MSBuild 可在 64 位元處理序中執行建置工作，以鎖定 64 位元電腦。 這是由 `UsingTask` 引數和 `Task` 參數所控制。 .NET Framework 4.5 所安裝的目標會設定這些引數和參數，而且不需進行變更就能為各種目標內容建置應用程式。  
  
 如果您要建立自己的目標內容，則必須適當設定這些引數和參數。 如需範例，請查看 .NET Framework 4.5 Microsoft.Common.targets 檔案和 Microsoft.Common.Tasks 檔案。  如需如何建立可處理多個目標內容的自訂工作或如何修改現有工作的資訊，請參閱[如何：設定目標和工作](../msbuild/how-to-configure-targets-and-tasks.md)。  
  
## <a name="see-also"></a>請參閱  
 [多目標](../msbuild/msbuild-multitargeting-overview.md)
