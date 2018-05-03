---
title: 在 Visual Studio 中檢視用於負載測試的資料和診斷附件
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2bed9c90bb7562072c2f0855c361fc307227976d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>如何：使用負載測試分析器檢視資料和診斷附件

在執行負載測試之前，您可以選取測試設定，指定要使用的診斷和資料配接器。 在負載測試完成之後，當您分析結果時，可以使用 [負載測試分析器] 來檢視這些診斷和資料配接器的詳細資料。 若要檢視資料和診斷配接器的詳細資料，請選擇 [負載測試分析器] 工具列上的 [檢視資料和診斷附件] 按鈕。 例如，如果負載測試的測試設定中有設定系統資訊配接器，您就可以檢視用於執行負載測試之電腦的系統資訊。

![選擇 [診斷資料配接器附件] 對話方塊](../test/media/load_adapterdialog.png "Load_AdapterDialog")

另一個例子是負載測試的測試設定中包含 IntelliTrace 配接器。 IntelliTrace 配接器可讓您開啟 [IntelliTrace 摘要] 頁面。

![IntelliTrace 摘要](../test/media/load_intellitrace.png "Load_IntelliTrace")

如需詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)和[收集 IntelliTrace 資料](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)。

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>若要從負載測試分析器檢視負載測試中的資料和診斷附件

1.  在負載測試完成之後，或當您開啟負載測試結果之後，請選擇 [負載測試分析器] 工具列上的 [檢視資料和診斷附件]。

     [選擇診斷資料配接器] 對話方塊隨即顯示。

2.  選取您要分析的診斷資料配接器附件，然後選擇 [確定]。

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)