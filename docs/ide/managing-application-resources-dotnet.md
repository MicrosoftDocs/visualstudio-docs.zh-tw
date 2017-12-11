---
title: "管理應用程式資源 (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>管理應用程式資源 (.NET)
資源檔案是屬於應用程式的一部分，但不會經過編譯的檔案，例如圖示檔案或音訊檔案。 由於這些檔案不屬於編譯處理程序的一部分，您可以變更它們而無需重新編譯二進位檔。 如果您打算將應用程式當地語系化，您應該針對所有字串和其他在將應用程式當地語系化時需要變更的資源使用資源檔。  
  
如需 .NET 桌面應用程式中的資源的詳細資訊，請參閱 [Resources in Desktop Apps](/dotnet/framework/resources/index)。 如需 C++ 桌面應用程式中的資源的詳細資訊，請參閱 [Working with Resource Files](/cpp/windows/working-with-resource-files)。  
  
UWP 應用程式使用的資源模型與桌面應用程式不同。 如需 Windows 8.x 應用程式中資源的資訊，請參閱[定義應用程式資源 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx)。  
  
## <a name="working-with-resources"></a>使用資源  
在 受控碼專案中，開啟 [專案屬性] 視窗。 您可以透過下列方式開啟 [屬性] 視窗：

- 在方案總管中，以滑鼠右鍵按一下專案節點，並選取 [屬性]
- 在 [快速啟動] 視窗中，鍵入**專案屬性**
- 選擇方案總管視窗中的 **Alt + Enter**

選取 **資源**  索引標籤。您可以在專案尚未包含 .resx 檔案的情況下加入 .resx 檔案、加入和刪除不同種類的資源，以及修改現有的資源。  
  
若要了解如何在 C++ 專案中使用資源，請參閱 [How to: Create a Resource](/cpp/windows/how-to-create-a-resource)。