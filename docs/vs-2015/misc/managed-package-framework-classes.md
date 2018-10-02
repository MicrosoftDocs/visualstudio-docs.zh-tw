---
title: Managed 封裝架構類別 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498271"
---
# <a name="managed-package-framework-classes"></a>Managed 封裝架構類別
Managed 封裝架構 (MPF) 類別可用來使用 Managed 程式碼建立 VSPackage。 它們提供許多 VSPackage 介面的預設實作。 藉由隱藏實作詳細資料和複雜性，MPF 可讓您建立[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合產品，最少的程式碼。  
  
> [!WARNING]
>  Visual Studio SDK 附有大部分包含 Managed 封裝架構類別的組件。 您可以在 [適用於專案的 Managed 封裝架構](http://mpfproj11.codeplex.com/)中下載適用於專案的 Managed 封裝架構原始程式碼。  
  
## <a name="mpf-namespaces"></a>MPF 命名空間  
 下表列出所提供的 MPF 命名空間[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]。  
  
|命名空間|內容|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|包含處理 COM 錯誤的有用類別[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]常數和 Win32 視窗。|  
|<xref:Microsoft.VisualStudio.Package>|包含的 managed 程式碼包裝函式[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案、 編輯器和 MSBuild。|  
|<xref:Microsoft.VisualStudio.Shell>|包括 MPF 基底類別，您可以從中衍生許多常見 Visual Studio 物件的實作。|  
|<xref:Microsoft.VisualStudio.Shell.Design>|包含[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]設計工具擴充功能。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|包含[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]序列化設計工具擴充功能。|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|包含[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]CodeDom 設計工具擴充功能。|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|支援專案子類型 (也稱為「類別」)。|  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 和 Managed 的封裝架構](../misc/vspackages-and-the-managed-package-framework.md)   
 [使用 Visual Studio Interop 組件](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackage 和 Managed 封裝架構](../misc/vspackages-and-the-managed-package-framework.md)