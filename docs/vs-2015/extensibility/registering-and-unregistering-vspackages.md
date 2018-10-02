---
title: 註冊及取消註冊 Vspackage |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8995bbb47f9a65a101256029a28313768a0b04ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489232"
---
# <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[註冊和取消註冊 Vspackage](https://docs.microsoft.com/visualstudio/extensibility/registering-and-unregistering-vspackages)。  
  
您可以使用屬性來註冊 VSPackage，但  
  
## <a name="registering-a-vspackage"></a>註冊 VSPackage  
 您可以使用屬性來控制 managed Vspackage 的註冊。 所有的註冊資訊會包含在.pkgdef 檔。 如需有關檔案為基礎的註冊的詳細資訊，請參閱[CreatePkgDef 公用程式](../extensibility/internals/createpkgdef-utility.md)。  
  
 下列程式碼示範如何使用標準的註冊屬性來註冊 VSPackage。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>取消註冊擴充功能  
 如果您已進行實驗，具有許多不同的 Vspackage，而且想要移除的實驗執行個體，您就可以執行**重設**命令。 尋求**重設 Visual Studio 的實驗執行個體**在您的電腦，[開始] 頁面上，或從命令列執行此命令：  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要解除安裝的擴充功能，您已安裝 Visual Studio 的開發執行個體上，請移至**工具 / 擴充功能和更新**，找延伸模組，然後按**解除安裝**。  
  
 如果基於某些原因，這些方法都不成功在解除安裝擴充功能，可以取消註冊 VSPackage 組件，從命令列，如下所示：  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)

