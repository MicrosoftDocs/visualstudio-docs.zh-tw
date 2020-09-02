---
title: Managed Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, managed
- managed VSPackages
ms.assetid: a4f17068-c563-45a8-bbbf-4203ea99e9d2
caps.latest.revision: 34
manager: jillfra
ms.openlocfilehash: bde7742bc9165413abcf98bfb475c19ec0e45f51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62838759"
---
# <a name="managed-vspackages"></a>Managed VSPackage
下列主題說明如何建立 VSPackage。 VSPackage 是一種軟體模組，藉 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 由提供使用者介面 (UI) 元素、服務、專案、編輯器和設計工具，來擴充整合式開發環境 (IDE) 。 如需詳細資訊，請參閱 [VSPackages](../extensibility/internals/vspackages.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 Visual Studio Interop 組件](../extensibility/internals/using-visual-studio-interop-assemblies.md)  
 描述 interop 元件的函式和位置 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，以及它們所提供的命名空間。  
  
 [Managed 程式碼中的 HRESULT 資訊](../misc/hresult-information-in-managed-code.md)  
 討論如何將 HRESULT 資訊轉譯成擲回的例外狀況，並 `int` 在 managed 程式碼中傳回值。  
  
 [Visual Studio Interop 組件參數封送處理](../misc/visual-studio-interop-assembly-parameter-marshaling.md)  
 討論 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件和 COM 介面之間的互通性問題。  
  
 [VSPackage 和 Managed 封裝架構](../misc/vspackages-and-the-managed-package-framework.md)  
 描述和列出 managed package framework (MPF) 類別命名空間和 DLL 檔案，並示範如何使用它們來建立 VSPackage。  
  
 [VSPackage 中的資源](../extensibility/internals/resources-in-vspackages.md)  
 描述 managed Vspackage 中受控和非受控資源的使用方式。  
  
## <a name="related-sections"></a>相關章節  
 [VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md)  
 提供 VSPackage 內部和 advanced 主題的集合。