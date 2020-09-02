---
title: 使用工具視窗建立延伸模組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431845"
---
# <a name="creating-an-extension-with-a-tool-window"></a>使用工具視窗建立延伸模組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在此程式中，您將瞭解如何使用 VSIX 專案範本和 **自訂工具視窗** 專案範本，以使用工具視窗建立延伸模組。  
  
## <a name="prerequisites"></a>Prerequisites  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="creating-a-tool-window"></a>建立工具視窗  
  
1. 建立名為 **FirstWindow**的 VSIX 專案。 您可以在 [ **新增專案** ] 對話方塊中的 **Visual c #/** 擴充性下找到 VSIX 專案範本。  
  
2. 當專案開啟時，加入名為 **FirstWindow**的工具視窗專案範本。 在 [ **方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [ **加入/新專案**]。 在 [ **加入新專案** ] 對話方塊中，移至 [ **Visual c #/** 擴充性] 並選取 [ **自訂工具視窗]**。 在視窗底部的 [ **名稱** ] 欄位中，將工具視窗的檔案名變更為 **FirstWindow.cs**。  
  
3. 建置此專案並開始偵錯。  
  
     Visual Studio 的實驗實例隨即出現。 如需實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。  
  
4. 在實驗性實例中，移至 [ **View]/[其他視窗**]。  
  
     您應該會看到 **FirstWindow**的功能表項目。 按一下此按鈕。  
  
     您應該會看到一個具有標題**FirstWindow**的工具視窗，以及一個指出**Click Me！** 的按鈕。
