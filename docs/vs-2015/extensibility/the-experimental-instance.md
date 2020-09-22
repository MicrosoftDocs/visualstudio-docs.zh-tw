---
title: 實驗實例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838861"
---
# <a name="the-experimental-instance"></a>實驗執行個體
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

為了保護您的 Visual Studio 開發環境免于可能變更的未測試應用程式，VSSDK 提供了實驗性的空間，讓您可以用來進行實驗。 您可以像往常一樣使用 Visual Studio 來開發新的應用程式，但您可以使用此實驗性實例來執行這些應用程式。  
  
 具有 VSIX 封裝的每個應用程式會在「偵錯工具」模式中啟動 Visual Studio 實驗實例。  
  
 如果您想要在特定解決方案之外啟動 Visual Studio 的實驗性實例，請在命令視窗中執行下列命令：  
  
 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/RootSuffix Exp  
  
> [!NOTE]
> 實驗實例會寫入至和節點下的登錄 `<version number>Exp` `<version number>Exp_Config` 。 例如，Visual Studio 2015 實驗登錄區是  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 建議您在開發時，于實驗實例中執行您的擴充功能。 當您部署擴充功能時，它會在開發實例中執行。 如需註冊應用程式的詳細資訊，請參閱 [註冊 vspackage](../extensibility/internals/registering-vspackages.md)。
