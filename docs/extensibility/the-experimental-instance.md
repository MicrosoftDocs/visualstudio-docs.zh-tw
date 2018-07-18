---
title: 實驗執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138921"
---
# <a name="the-experimental-instance"></a>實驗執行個體
為了保護您的 Visual Studio 開發環境，從未經測試的應用程式，可能會變更，VSSDK 會提供您可用來試用實驗空間。 您像往常一樣，使用 Visual Studio 來開發新的應用程式，但您執行使用此實驗執行個體。  
  
 有 VSIX 封裝每個應用程式會啟動偵錯模式中的 Visual Studio 實驗執行個體。  
  
 如果您想要開始在特定的方案之外的 Visual Studio 的實驗執行個體，請在命令視窗執行下列命令：  
  
 「*\<Visual studio 安裝路徑 >* \Common7\IDE\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  實驗執行個體底下的登錄寫入`<version number>Exp`和`<version number>Exp_Config`節點。 比方說是 Visual Studio 2015 實驗登錄區  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 我們建議您在實驗執行個體中執行您的擴充功能，在開發過程。 當您部署擴充功能時，它會執行開發執行個體中。 如需有關如何註冊應用程式的詳細資訊，請參閱[註冊 Vspackage](../extensibility/internals/registering-vspackages.md)。