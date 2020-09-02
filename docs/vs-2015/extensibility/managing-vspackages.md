---
title: 管理 Vspackage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194382"
---
# <a name="managing-vspackages"></a>管理 VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在大多數情況下，您不需要擔心管理 Vspackage，因為專案和專案範本會自動註冊和載入封裝。 不過，在某些情況下，您可能需要更多的學習，才能管理您的封裝。  
  
## <a name="using-the-experimental-instance"></a>使用實驗實例  
 若要瞭解實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 VSPackage  
 若要瞭解如何註冊及取消註冊 Vspackage 和其他類型的延伸模組，請參閱 [註冊和取消註冊 vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>載入 VSPackage  
 當特定 CMDUICONTEXT GUID 開啟時，可以將 Vspackage 設定為自動載入。 如需詳細資訊，請參閱 [載入 vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>在背景中使用 AsyncPackage 載入 Vspackage  
 AsyncPackage 類別可讓您在背景執行緒上載入封裝，以提升 Visual Studio 中的 UI 回應性。 如需詳細資訊，請參閱 [如何：在背景中使用 AsyncPackage 載入 vspackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>延伸模組的以規則為基礎的 UI 內容  
 以規則為基礎的 UI 內容，可讓延伸模組作者定義啟用 UI 內容並載入相關聯 Vspackage 的精確條件。 如需詳細資訊，請參閱 [如何：使用 Visual Studio 擴充功能的以規則為基礎的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="troubleshooting-vspackages"></a>針對 VSPackage 進行疑難排解  
 瞭解針對未載入或發生錯誤之 Vspackage 進行疑難排解的技術： [疑難排解 vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另請參閱  
 [VSPackages](../extensibility/internals/vspackages.md)
