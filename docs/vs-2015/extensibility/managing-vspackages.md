---
title: 管理 Vspackage |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b68ad8fb8ce32c2a4a1210d38fb458518d28435
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296344"
---
# <a name="managing-vspackages"></a>管理 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在大部分情況下，您不必擔心管理 Vspackage，因為專案和項目範本註冊，並自動載入封裝。 不過，在某些情況下，您可能需要了解更多的資訊，以管理您的封裝。  
  
## <a name="using-the-experimental-instance"></a>使用實驗性執行個體  
 若要深入了解實驗執行個體，請參閱[實驗的執行個體](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 VSPackage  
 若要了解如何註冊和取消註冊 Vspackage 和其他類型的擴充功能，請參閱[註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>正在載入 VSPackage  
 Vspackage 可以自動載入 CMDUICONTEXT GUID 開啟某一特定設定。 如需詳細資訊，請參閱 <<c0> [ 載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>使用 AsyncPackage 載入 Vspackage 在背景中  
 AsyncPackage 類別可讓您更好的 UI 回應性，在 Visual Studio 中的背景執行緒上載入的封裝。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 AsyncPackage 載入 vspackage 在背景中](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>延伸模組的規則為基礎的 UI 內容  
 以規則為基礎的 UI 內容可讓延伸模組作者定義用以啟動 UI 內容，以及相關聯的 Vspackage 載入的精確條件。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用規則式 Visual Studio 擴充功能的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="troubleshooting-vspackages"></a>針對 VSPackage 進行疑難排解  
 了解針對 Vspackage 未載入或發生錯誤進行疑難排解的技術：[疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)

