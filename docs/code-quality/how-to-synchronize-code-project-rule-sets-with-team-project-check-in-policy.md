---
title: 使用簽入原則同步處理專案規則集
ms.date: 11/04/2016
description: 瞭解如何同步處理 Visual Studio 程式碼專案規則集與 Azure DevOps 專案簽入原則。
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2908f7ec93d8704b52798121bd0076a7f5fddc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859914"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>如何：使用 Azure DevOps 專案簽入原則來同步處理常式代碼專案規則集

您可以指定規則集，其中至少包含在簽入原則的規則集中指定的規則，藉以將程式碼專案的程式碼分析設定同步處理至 Azure DevOps 專案的簽入原則。 您的開發人員負責人可以通知您簽入原則的規則集名稱和位置。 您可以使用下列其中一個選項，以確保專案的程式碼分析使用正確的規則集：

- 如果簽入原則使用其中一個 Microsoft 內建規則集，請開啟程式碼專案的 [屬性] 對話方塊，並顯示 [程式碼分析] 頁面，然後選取規則集。 系統會自動安裝 Microsoft 標準規則集，並將 Visual Studio 設定為唯讀，且不應該編輯。 如果未編輯規則集，原則和本機規則集中的規則保證會相符。

- 如果簽入原則使用自訂規則集，請在版本控制中的規則集檔案上執行取得作業，以建立本機複本。 然後在程式碼專案的程式碼分析設定中指定本機位置。 如果簽入原則的規則集是最新的，則規則會保證相符。

     如果您將版本控制位置對應到 Azure DevOps 專案根目錄與程式碼專案相同關聯性的本機資料夾，則會使用相對路徑來設定規則的位置。 相對路徑可確保程式碼分析的程式碼專案設定可移至其他電腦。

- 針對程式碼專案的簽入原則自訂規則集的複本。 請確定新的規則集包含簽入原則中的所有規則，以及您想要包含的任何其他規則。 您必須確定您的規則集包含簽入原則規則集中的所有規則。

## <a name="to-specify-a-microsoft-standard-rule-set"></a>若要指定 Microsoft 標準規則集

1. 在 **方案總管** 中，以滑鼠右鍵按一下程式碼專案，然後按一下 [ **屬性**]。

2. 按一下 [程式碼分析]。

::: moniker range="vs-2017"

3. 在 [ **執行此規則集** ] 清單中，選取 [簽入原則規則集]。

::: moniker-end

::: moniker range=">=vs-2019"

3. 在 [作用中 **規則** ] 清單中，選取 [簽入原則規則集]。

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>若要指定自訂簽入原則規則集

1. 如有必要，請在指定簽入原則的規則集檔案上執行 get 作業。

2. 在 **方案總管** 中，以滑鼠右鍵按一下程式碼專案，然後按一下 [ **屬性**]。

3. 按一下 [程式碼分析]。

::: moniker range="vs-2017"

4. 在 [ **執行此規則集** ] 清單中，按一下 **\<Browse>** 。

::: moniker-end

::: moniker range=">=vs-2019"

4. 在 [作用中 **規則** ] 清單中，按一下 **\<Browse>** 。

::: moniker-end

5. 在 [ **開啟** ] 對話方塊中，指定簽入原則規則集檔案。

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>若要建立程式碼專案的自訂規則集

如需有關建立自訂規則集的詳細資訊，請參閱 [自訂規則集](how-to-create-a-custom-rule-set.md)。
