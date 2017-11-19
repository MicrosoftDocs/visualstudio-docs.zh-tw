---
title: "建立擴充功能與工具視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cda2d9bc4bde1c0bf9d9dd82c48864725f0e25f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>建立擴充功能與工具視窗
在此程序，您會了解如何使用 VSIX 專案範本和**自訂工具視窗**項目範本建立的擴充功能與工具視窗。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="creating-a-tool-window"></a>建立工具視窗  
  
1.  建立 VSIX 專案，名為**FirstWindow**。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  當專案開啟時，加入名為的工具視窗項目範本**MyWindow**。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂工具視窗**。 在**名稱**在視窗底部的欄位、 變更工具視窗的檔案名稱，以**MyWindow.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需實驗執行個體的詳細資訊，請參閱[實驗執行個體的](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，移至**檢視 / 其他視窗**。  
  
     您應該會看到的功能表項目**MyWindow**。 按一下它。  
  
     您應該會看到工具視窗的標題**MyWindow**和按鈕，指出**Click Me ！。**