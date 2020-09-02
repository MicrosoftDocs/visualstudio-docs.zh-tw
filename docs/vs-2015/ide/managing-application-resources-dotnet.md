---
title: 管理應用程式資源 (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651378"
---
# <a name="managing-application-resources-net"></a>管理應用程式資源 (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

資源檔案是屬於應用程式的一部分，但不會經過編譯的檔案，例如圖示檔案或音訊檔案。 由於這些檔案不屬於編譯處理程序的一部分，您可以變更它們而無需重新編譯二進位檔。 如果您打算將應用程式當地語系化，您應該針對所有字串和其他在將應用程式當地語系化時需要變更的資源使用資源檔。

 如需 .NET 桌面應用程式中的資源的詳細資訊，請參閱 [Resources in Desktop Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)。 如需 C++ 桌面應用程式中的資源的詳細資訊，請參閱 [Working with Resource Files](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780)。

 Windows 市集應用程式使用的資源模型與桌面應用程式不同。 如需 Windows 市集應用程式中的資源的相關資訊，請參閱 Windows 開發人員中心網站上的 [定義應用程式資源](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) 。

## <a name="working-with-resources"></a>使用資源
 在 managed 程式碼專案中，開啟 [專案屬性] 視窗 (以滑鼠右鍵按一下專案節點中的 **方案總管] 中** ，然後選取 **屬性**, ，或類型 **專案屬性** 中 **快速啟動** ] 視窗中，或輸入 ALT + ENTER 在 **方案總管] 中** 視窗)。 選取 [ **資源** ] 索引標籤。如果您的專案尚未包含 .resx 檔案，您可以新增和刪除不同種類的資源，以及修改現有的資源。

 若要了解如何在 C++ 專案中使用資源，請參閱 [How to: Create a Resource](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716)。
