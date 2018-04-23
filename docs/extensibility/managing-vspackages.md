---
title: 管理 Vspackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e3241bae84b89b53e30c3d0949e4f8551110e7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="managing-vspackages"></a>管理 Vspackage
在大部分情況下，您不必擔心管理 Vspackage，因為專案和項目範本的註冊，並自動載入封裝。 不過，在某些情況下，您可能需要了解更多的位元，以管理您的封裝。  
  
## <a name="using-the-experimental-instance"></a>使用實驗性執行個體  
 若要了解有關實驗執行個體的詳細資訊，請參閱[實驗執行個體的](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>註冊和取消登錄 Vspackage  
 若要了解如何註冊及取消註冊 Vspackage 和其他類型的擴充功能，請參閱[註冊和取消登錄 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>載入 VSPackage  
 Vspackage 可以將 autoload 設定某一特定 CMDUICONTEXT GUID 已開啟。 如需詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>若要載入 Vspackage 在背景中的使用 AsyncPackage  
 AsyncPackage 類別可讓 Visual Studio 中更好的 UI 回應性的背景執行緒上載入的封裝。 如需詳細資訊，請參閱[How to： 在背景中載入 vspackage 使用 AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>延伸模組的規則為基礎的 UI 內容  
 以規則為基礎的 UI 內容可讓您定義的精確條件，程式就會啟動 UI 內容和相關聯的 Vspackage 載入的延伸模組作者。 如需詳細資訊，請參閱[How to： 使用規則為基礎的 Visual Studio 擴充功能的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="diagnosing-extension-performance"></a>診斷延伸模組的效能  
擴充功能可能會影響啟動及方案負載的效能。 了解 Visual Studio 擴充功能影響計算的方式以及它可以分析方式在本機以測試擴充功能可能會顯示為效能，從而影響擴充功能。 如需詳細資訊，請參閱[如何： 診斷延伸模組效能](how-to-diagnose-extension-performance.md)。 
  
## <a name="troubleshooting-vspackages"></a>疑難排解 Vspackage  
 了解 Vspackage 不會載入或發生錯誤的疑難排解的技術：[疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)