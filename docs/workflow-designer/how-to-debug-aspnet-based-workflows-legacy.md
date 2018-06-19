---
title: 工作流程設計工具-如何： 偵錯 ASP.NET 型工作流程 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975868"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>HOW TO：ASP.NET 工作流程偵錯 (舊版)

本主題描述如何偵錯 ASP.NET 型 Windows Workflow Foundation (WF) 應用程式，目標是.NET Framework 3.5 版或舊版的 Windows 工作流程設計工具中 WinFX。

您可以針對在 ASP.NET 中啟動的舊版工作流程，或是藉由附加至裝載工作流程的處理序而發行為 Web 服務的舊版工作流程進行偵錯。

## <a name="to-debug-an-aspnet-based-workflow"></a>若要偵錯 ASP.NET 工作流程

1.  啟用偵錯 ASP.NET 應用程式，藉由設定**偵錯 = true** web.config 檔案中。

2.  將工作流程程式庫設為啟始專案，並在工作流程中設定中斷點。

3.  在工作流程專案屬性中輸入預設網頁的 URL**偵錯**選項**與外部 URL 啟動瀏覽器**文字方塊。

4.  選取**附加至處理序**上**偵錯**功能表。

5.  選取要從附加至處理序**可用的處理序**清單。

     附加至裝載工作流程的 w3wp.exe、webdev.webserver 或 aspnet_wp 處理序。

6.  按一下**選取**旁**附加至**文字方塊。

     **選取程式碼類型** 對話方塊隨即出現。

7.  選取**偵錯這些程式碼類型**選取**工作流程**。

8.  按一下 [確定 **Deploying Office Solutions**]。

9. 按一下 [附加] 。

10. 在瀏覽器中開啟預設網頁，並啟動工作流程。

## <a name="see-also"></a>另請參閱

- [叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [如何：在工作流程中設定中斷點 (舊版)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)