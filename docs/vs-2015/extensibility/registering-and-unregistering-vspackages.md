---
title: 註冊和取消註冊 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193823"
---
# <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用屬性來註冊 VSPackage，但是  
  
## <a name="registering-a-vspackage"></a>註冊 VSPackage  
 您可以使用屬性來控制受控 Vspackage 的註冊。 所有註冊資訊都包含在 .pkgdef 檔案中。 如需以檔案為基礎之註冊的詳細資訊，請參閱 [CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。  
  
 下列程式碼說明如何使用標準註冊屬性來註冊您的 VSPackage。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>取消註冊擴充功能  
 如果您已經試驗過許多不同的 Vspackage，而且想要從實驗性實例中移除它們，您可以直接執行 **Reset** 命令。 在電腦的 [開始] 頁面上尋找 **[重設 Visual Studio 實驗實例** ]，或從命令列執行下列命令：  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要卸載 Visual Studio 開發實例上所安裝的擴充功能，請移至 [ **工具/擴充功能和更新**]，尋找擴充功能，然後按一下 [ **卸載**]。  
  
 如果基於某些原因，這兩種方法都無法在卸載擴充功能的情況下成功，您可以從命令列取消註冊 VSPackage 元件，如下所示：  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPackages](../extensibility/internals/vspackages.md)
