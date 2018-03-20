---
title: "安裝 Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 17b3b0a107d263a213746a625ec5a65419695b4d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK
Visual Studio SDK 是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>安裝 Visual Studio SDK 安裝的 Visual Studio 的一部分  
 如果您想要包含在 Visual Studio 安裝的 VSSDK，您應該安裝**Visual Studio 擴充功能開發**工作負載下的**其他工具組**。 這會安裝 Visual Studio SDK，以及所需的必要條件。 您可以進一步微調安裝，選取或取消選取的元件從摘要檢視。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝 Visual Studio 安裝 Visual Studio SDK  
 如果您決定要完成您的 Visual Studio 安裝之後，安裝 Visual Studio SDK，請重新執行 Visual Studio 安裝，然後選取**Visual Studio 擴充功能開發**工作負載。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>從方案安裝 Visual Studio SDK  
 如果您與擴充性專案中開啟的方案，但是未先安裝的 VSSDK，系統會提示您反白顯示的資訊列上方 [方案總管]。 它看起來應該像下面這樣：  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK  
因為任何 Visual Studio 工作負載或元件，您也可以安裝**Visual Studio 擴充功能開發**工作負載 (識別碼： Microsoft.VisualStudio.Workload.VisualStudioExtension) 從命令列。 請參閱[使用命令列參數來安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)如需判斷工作負載或元件的識別項的一般指示與適當的命令列參數的詳細資訊。
  
 請注意，您必須使用符合您已安裝的 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您尚未在電腦上安裝 Visual Studio Enterprise，您必須執行 Visual Studio 企業版安裝程式 (vs_enterprise.exe)。