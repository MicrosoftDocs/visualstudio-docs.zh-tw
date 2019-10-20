---
title: 如何：將程式碼專案規則集與 Team 專案簽入原則同步處理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651592"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>如何：同步處理具有 Team 專案簽入原則的程式碼專案規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由指定規則集，將程式碼專案的程式碼分析設定同步處理至 team 專案的簽入原則，其方式是在簽入原則的規則集中指定至少包含規則。 您的開發人員主管可以通知您簽入原則的規則集名稱和位置。 您可以使用下列其中一個選項，以確保專案的程式碼分析會使用正確的規則集：

- 如果簽入原則使用其中一個 Microsoft 內建規則集，請開啟程式碼專案的 [屬性] 對話方塊，顯示 [程式碼分析] 頁面，然後在程式碼專案設定的 [程式碼分析] 頁面上選取規則集。 Microsoft standard 規則集會自動安裝，Visual Studio 設定為唯讀且不應編輯。 如果未編輯規則集，則會保證原則和本機規則集中的規則會符合。

- 如果簽入原則使用自訂規則集，請在版本控制中的規則集檔案上執行 get 作業，以建立本機複本。 然後在程式碼專案的程式碼分析設定中指定該本機位置。 如果簽入原則的規則集是最新狀態，則保證規則會相符。

     如果您將版本控制位置對應至與 team 專案根目錄相同的本機資料夾，做為您的程式碼專案，則會使用相對路徑來設定規則的位置。 相對路徑可確保程式碼分析的程式碼專案設定可移至其他電腦。

- 針對程式碼專案的簽入原則自訂規則集的複本。 請確定新的規則集包含簽入原則中的所有規則，以及您想要包含的任何其他規則。 您必須確定您的規則集包含簽入原則之規則集中的所有規則。

### <a name="to-specify-a-microsoft-standard-rule-set"></a>若要指定 Microsoft standard 規則集

1. 在**方案總管**中，以滑鼠右鍵按一下程式碼專案，然後按一下 [**屬性**]。

2. 按一下 [程式**代碼分析**]。

3. 在 [**執行此規則集**] 清單中，按一下 [簽入原則] 規則集。

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>若要指定自訂簽入原則規則集

1. 如有必要，請在指定簽入原則的規則集檔案上執行 get 作業。

2. 在**方案總管**中，以滑鼠右鍵按一下程式碼專案，然後按一下 [**屬性**]。

3. 按一下 [程式**代碼分析**]。

4. 在 **執行此規則集** 清單中，按一下  **\<Browse .。。>** 。

5. 在 [**開啟**] 對話方塊中，指定簽入原則規則集檔案。

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>若要建立程式碼專案的自訂規則集

1. 遵循本主題稍早的其中一個程式，在 [專案設定] 對話方塊的 [程式碼分析] 頁面上，選取 team 專案的簽入原則。

2. 按一下 [開啟]。

3. 使用 [規則集編輯器] 來新增或移除規則。

     如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。

4. 將修改過的規則集儲存到本機電腦或 UNC 路徑上的規則集檔案。

5. 開啟程式碼專案的 [屬性] 對話方塊，然後顯示 [程式**代碼分析**] 頁面。

6. 在 **執行此規則集** 清單中，按一下  **\<Browse .。。>** 。

7. 在 [**開啟**] 對話方塊中，指定規則集檔案。
