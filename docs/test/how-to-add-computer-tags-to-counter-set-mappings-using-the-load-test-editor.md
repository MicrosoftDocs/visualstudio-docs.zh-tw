---
title: 在 Visual Studio 中為負載測試將電腦標記新增至計數器集合對應
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d6b14ef4ae42ef978c449f7cb4bafaa08bf8a1a6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>如何：使用負載測試編輯器將電腦標記加入至計數器集合對應

電腦標記可讓您使用容易辨識的名稱來識別電腦。 這些標記會顯示在 [負載測試編輯器] 樹狀目錄的 [計數器集合對應] 節點中。 更重要的是，這些標記會顯示在 Excel 報表中，可協助專案關係人識別電腦在負載測試中扮演的角色。 例如 "Web Server1 in lab2" 或 "SQL Server2 in Phoenix office"。 如需詳細資訊，請參閱[針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)。

## <a name="to-add-a-tag-to-a-computer"></a>若要將標記加入至電腦

1.  開啟負載測試。

2.  選擇 [管理計數器集合] 按鈕。

     -或-

     以滑鼠右鍵按一下負載測試樹狀目錄中的 [計數器集合] 資料夾，然後選擇 [管理計數器集合]。

     [管理計數器集合] 對話方塊隨即顯示。

3.  (選擇性) 在 [選取的電腦和計數器集合會新增至下列回合設定之下] 清單方塊中，選取不同的回合設定。

    > [!NOTE]
    > 這僅適用於您的負載測試中有一個以上的回合設定時。

4.  在 [要監視的電腦和計數器集合] 底下，選取要套用標記的電腦。

    > [!NOTE]
    > 如需如何新增電腦的資訊，請參閱[如何：管理計數器集合](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)。

5.  在 [電腦標記] 文字方塊中，鍵入要與電腦建立關聯的標記。 例如，"TestMachine12 in lab3"。

6.  選擇 [確定] 。

## <a name="see-also"></a>另請參閱

- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [如何：管理計數器集合](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)