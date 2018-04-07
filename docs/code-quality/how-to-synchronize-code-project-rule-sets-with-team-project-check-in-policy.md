---
title: 如何： 同步處理具有 Team 專案簽入原則的程式碼專案規則集 |Microsoft 文件
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 77a619178001ef95f5d19d80abda5c4ab2237a0f
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>如何：同步處理具有 Team 專案簽入原則的程式碼專案規則集

您可以同步至 team 專案的簽入原則的程式碼專案的程式碼分析設定藉由指定規則集，其中至少包含簽入原則設定的規則中指定的規則。 開發負責人可以通知您的名稱和位置的規則集簽入原則。 您可以使用下列選項的其中一個為確保程式碼分析專案會使用一組正確的規則：

-   簽入原則可以使用其中一個 Microsoft 內建規則集，如果開啟程式碼專案的 內容 對話方塊，顯示程式碼分析 頁面中，然後選取的程式碼專案設定程式碼分析 頁面上設定的規則。 Microsoft 標準規則集會隨 Visual Studio 自動安裝設定為唯讀，並不應編輯。 如果不編輯規則集時，保證的原則和本機規則集合中的規則比對。

-   如果在簽入原則使用自訂規則集，執行規則集檔案上的 get 作業中版本控制，以便建立本機複本。 在程式碼專案的程式碼分析設定，然後指定該本機位置。 符合最新狀態的規則集簽入原則是否一定的規則。

     如果您的版本控制的位置對應至本機資料夾中的相同關聯性 team 專案的根目錄為您的程式碼專案時，規則的位置會設定使用相對路徑。 相對路徑，可確保程式碼分析的程式碼專案設定，可以移至其他電腦。

-   自訂的規則集的程式碼專案的簽入原則的複本。 請確定新的規則集包含在簽入原則中的所有規則和您想要包含的任何其他規則。 您必須確定規則集包含的所有規則，在簽入原則設定的規則。

## <a name="to-specify-a-microsoft-standard-rule-set"></a>若要指定 Microsoft 標準規則設定

1.  在**方案總管 中**，程式碼專案，以滑鼠右鍵按一下，然後按一下**屬性**。

2.  按一下**程式碼分析**。

3.  在**執行此規則集**清單中，按一下 簽入原則規則集。

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>若要指定自訂簽入原則規則設定

1.  如有必要，執行 get 作業指定的簽入原則的規則集檔案。

2.  在**方案總管 中**，程式碼專案，以滑鼠右鍵按一下，然後按一下**屬性**。

3.  按一下**程式碼分析**。

4.  在**執行此規則集**清單中，按一下**\<瀏覽 >**。

5.  在**開啟**對話方塊方塊中，指定簽入原則規則集檔案。

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>若要建立自訂規則設定程式碼專案

1.  請依照下列其中一個程序稍早在本主題來選取在專案的 [設定] 對話方塊的 [程式碼分析] 頁面上的 team 專案的簽入原則中。

2.  按一下**開啟**。

3.  新增或移除規則使用[規則集編輯器](../code-quality/working-in-the-code-analysis-rule-set-editor.md)。

4.  儲存修改過的規則設定為.ruleset 檔案在本機電腦或 UNC 路徑。

5.  開啟 [內容] 對話方塊的程式碼專案，並顯示**程式碼分析**頁面。

6.  在**執行此規則集**清單中，按一下**\<瀏覽 >**。

7.  在**開啟**對話方塊方塊中，指定規則集檔案。