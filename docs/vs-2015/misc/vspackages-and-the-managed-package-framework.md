---
title: Vspackage 和 Managed Package Framework |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298230"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackage 和 Managed 封裝架構
您可以使用 managed package framework （MPF）類別來建立 VSPackage，而不是使用 COM Interop 類別，藉以縮短開發時間。  
  
 有兩種方式可建立受控 VSPackage：  
  
- 使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 封裝專案範本  
  
     如需詳細資訊，請參閱逐步解說[：使用 Visual Studio 封裝範本建立功能表命令](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)。  
  
- 不搭配 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Package 專案範本來建立您的 VSPackage  
  
     例如，您可以複製範例 VSPackage，並變更 Guid 和名稱。 
  
## <a name="in-this-section"></a>本節內容  
 [Managed 封裝架構類別](../misc/managed-package-framework-classes.md)  
 描述和列出 MPF 類別命名空間和 DLL 檔案。  
  
## <a name="related-sections"></a>相關章節  
 [逐步解說：使用 Visual Studio 封裝範本建立功能表命令](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 說明如何建立受控 VSPackage。  
  
 [Managed VSPackages](../misc/managed-vspackages.md)  
 介紹適用于 managed 程式碼的 Vspackage 層面。