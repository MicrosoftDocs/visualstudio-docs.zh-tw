---
title: 實驗執行個體 |Microsoft Docs
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
ms.openlocfilehash: 907b90f60ad2167b64e5a4ca8ff160190c625313
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939649"
---
# <a name="the-experimental-instance"></a>實驗執行個體
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

為了確保您的 Visual Studio 開發環境，從未經測試的應用程式可能會變更，請 VSSDK 提供實驗性的空間，可供您實驗。 像往常一樣，使用 Visual Studio 開發新的應用程式，但您使用此實驗的執行個體執行。  
  
 VSIX 封裝每個應用程式會啟動偵錯模式中的 Visual Studio 實驗執行個體。  
  
 如果您想要開始在特定的方案之外的 Visual Studio 實驗執行個體，請在命令視窗執行下列命令：  
  
 "*\<Visual studio installation path>* \Common7\IDE\devenv.exe" /RootSuffix Exp  
  
> [!NOTE]
>  實驗性的執行個體底下的登錄寫入`<version number>Exp`和`<version number>Exp_Config`節點。 例如 Visual Studio 2015 實驗登錄區是  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 我們建議您在實驗執行個體中執行您的延伸模組，在開發過程。 當您部署延伸模組時，它會在開發執行個體中執行。 如需有關如何註冊應用程式的詳細資訊，請參閱 <<c0> [ 註冊 Vspackage](../extensibility/internals/registering-vspackages.md)。
