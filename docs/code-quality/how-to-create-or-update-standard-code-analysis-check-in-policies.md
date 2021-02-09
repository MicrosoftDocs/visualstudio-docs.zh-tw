---
title: 建立/更新標準程式碼分析簽入原則
description: 瞭解如何確保程式碼分析在 Azure DevOps 專案中的所有程式碼專案上執行。 請參閱如何設定專案程式碼分析簽入原則。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d46ed89880c41cbcaa6982c386e2ff8f115f8de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860109"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>如何：建立或更新標準程式碼分析簽入原則

您可以使用程式碼分析簽入原則，要求在 Azure DevOps 專案中的所有程式碼專案上執行程式碼分析。 要求程式碼分析可以改善簽入程式碼基底的程式碼品質。

> [!NOTE]
> 只有當您使用 Team Foundation Server 時，才能使用此功能。

程式碼分析簽入原則會在專案設定中設定，並套用至每個程式碼專案。 程式碼分析執行是針對專案中的程式碼專案所設定 ( xxproj) 檔。 系統會在本機電腦上執行程式碼分析。 當您啟用程式碼分析簽入原則時，必須在最後一次編輯之後編譯要簽入之程式碼專案中的檔案，而且至少必須在進行變更的電腦上執行專案設定中的規則。

- 針對 managed 程式碼，您可以指定包含程式碼分析規則子集的 *規則集* ，以設定簽入原則。

- 針對 C/c + + 程式碼，在 Visual Studio 2017 15.6 版及更早版本中，簽入原則要求所有程式碼分析規則都必須執行。 您可以加入處理器前指示詞，以停用 Azure DevOps 專案中個別程式碼專案的特定規則。 在15.7 和更新版本中，您可以使用 **/analyze：規則集** 來指定要執行的規則。 如需詳細資訊，請參閱 [使用規則集指定要執行的 c + + 規則](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)。

當您指定 managed 程式碼的簽入原則之後，小組成員就可以將程式碼專案的程式碼分析設定同步處理至 Azure DevOps 專案原則設定。

## <a name="to-open-the-check-in-policy-editor"></a>開啟簽入原則編輯器

1. 在 Team Explorer 中，以滑鼠右鍵按一下專案名稱，指向 [ **專案設定**]，然後按一下 [ **原始檔控制**]。

1. 在 [ **原始檔控制** ] 對話方塊中，選取 [ **簽入原則** ] 索引標籤。

1. 執行下列其中一個動作：

    - 按一下 **[新增]** 以建立新的簽入原則。

    - 按兩下 [**原則類型**] 清單中的現有程式 **代碼分析** 專案，以變更原則。

## <a name="to-set-policy-options"></a>設定原則選項

選取或清除下列選項：

|選項|Description|
|------------|-----------------|
|**強制簽入只包含屬於目前方案的檔案。**|程式碼分析只能在方案和專案設定檔中指定的檔案上執行。 此原則可確保分析解決方案中的所有程式碼。|
|**強制執行 C/c + + 程式碼分析 (/analyze)**|需要以/analyze 編譯器選項建立所有 C 或 c + + 專案，才能在簽入之前先執行程式碼分析。|
|**強制執行 Managed 程式碼的程式碼分析**|要求所有 managed 專案都必須先執行程式碼分析和組建，才能簽入。|

## <a name="to-specify-a-managed-rule-set"></a>若要指定受控規則集

從 [ **執行此規則集** ] 清單中，使用下列其中一種方法：

- 選取 Microsoft 標準規則集。

- 按一下以選取自訂規則集 **\<Select Rule Set from Source Control...>** 。 然後，在原始檔控制瀏覽器中輸入規則集的版本控制路徑。 版本控制路徑的語法為：

   **$/** `TeamProjectName` **/** `VersionControlPath`

如需如何建立及執行自訂簽入原則規則集的詳細資訊，請參閱 [針對 Managed 程式碼執行自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)。

## <a name="see-also"></a>另請參閱

- [為受控碼實作自訂程式碼分析簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
