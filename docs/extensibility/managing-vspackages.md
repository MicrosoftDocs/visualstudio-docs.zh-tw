---
title: 管理 Vspackage |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: c07e3924db75f870910e22aee8c913f5a26a7411
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822287"
---
# <a name="manage-vspackages"></a>管理 Vspackage
在大部分情況下，您不必擔心管理 Vspackage，因為專案和項目範本註冊，並自動載入封裝。 不過，在某些情況下，您可能需要了解更多的資訊，以管理您的封裝。  
  
## <a name="use-the-experimental-instance"></a>使用實驗性執行個體  
 若要深入了解實驗執行個體，請參閱[實驗的執行個體](../extensibility/the-experimental-instance.md)。  
  
## <a name="register-and-unregister-vspackages"></a>註冊和取消註冊 Vspackage  
 若要了解如何註冊和取消註冊 Vspackage 和其他類型的擴充功能，請參閱[註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="load-a-vspackage"></a>載入 VSPackage  
 Vspackage 可以自動載入 CMDUICONTEXT GUID 開啟某一特定設定。 如需詳細資訊，請參閱 <<c0> [ 載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>使用 AsyncPackage 載入 Vspackage 在背景中  
 `AsyncPackage`類別可讓您更好的 UI 回應性，在 Visual Studio 中的背景執行緒上的封裝載入。 如需詳細資訊，請參閱[＜How to：使用 AsyncPackage 載入 Vspackage 在背景中](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>將 UI 內容規則為基礎的擴充功能  
 以規則為基礎的 UI 內容可讓延伸模組作者定義用以啟動 UI 內容，以及相關聯的 Vspackage 載入的精確條件。 如需詳細資訊，請參閱[＜How to：使用 Visual Studio 擴充功能的規則為基礎的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="diagnose-extension-performance"></a>診斷延伸模組的效能  
延伸模組可能會影響啟動和方案載入效能。 了解 Visual Studio 擴充功能影響的計算方式，以及如何進行分析在本機測試如果擴充功能可能會顯示為效能影響擴充功能。 如需詳細資訊，請參閱[＜How to：診斷延伸模組效能](how-to-diagnose-extension-performance.md)。 
  
## <a name="troubleshoot-vspackages"></a>針對 Vspackage 進行疑難排解  
 找出針對 Vspackage 未載入或發生錯誤進行疑難排解的技術：[針對 Vspackage 進行疑難排解](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)