---
title: 建立或更新標準程式碼分析簽入原則
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 768efb3e874f6427cd23f63f14671aa2db1bea71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816353"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>HOW TO：建立或更新標準程式碼分析簽入原則

您可以要求 Azure DevOps 專案中的所有程式碼專案上執行程式碼分析，使用程式碼分析簽入原則。 需要程式碼分析，可以改善簽入程式碼基底的程式碼的品質。

> [!NOTE]
> 只有當您使用 Team Foundation Server 時，才使用這項功能。

程式碼分析簽入原則套用至每個程式碼專案，並設定專案設定。 程式碼分析回合設定的程式碼專案的專案 (.xxproj) 檔案中的程式碼專案。 在本機電腦上執行程式碼分析回合。 將專案設定中的規則時啟用程式碼分析簽入原則、 其上次的編輯之後必須編譯要簽入程式碼專案中的檔案和包含執行的程式碼分析，至少必須執行的電腦上，變更已進行 s。

- 對於 managed 程式碼，您必須設定簽入原則藉由指定*規則集*，其中包含的程式碼分析規則子集。

- 適用於 C /C++程式碼，在 Visual Studio 2017 15.6 版及更早版本，簽入原則會要求所有的程式碼分析規則會執行。 您可以加入前置處理器指示詞，若要停用 Azure DevOps 專案中的個別程式碼專案的特定規則。 15.7 中和更新版本中，您可以使用 **/analyze: ruleset**指定要執行哪些規則。 如需詳細資訊，請參閱 <<c0> [ 指定来使用規則集C++要執行規則](using-rule-sets-to-specify-the-cpp-rules-to-run.md)。</c0>

指定 managed 程式碼簽入原則之後，小組成員可以同步處理他們的 Azure DevOps 專案原則設定的程式碼專案的程式碼分析設定。

## <a name="to-open-the-check-in-policy-editor"></a>若要開啟簽入原則編輯器

1. 在 Team Explorer 中，以滑鼠右鍵按一下專案名稱，指向**專案設定**，然後按一下**原始檔控制**。

1. 在 [**原始檔控制**對話方塊中，選取**簽入原則**] 索引標籤。

1. 執行下列任一步驟：

    - 按一下 **新增**，建立新的簽入原則。

    - 按兩下現有**程式碼分析**中的項目**原則類型**清單來變更原則。

## <a name="to-set-policy-options"></a>若要設定原則選項

選取或清除下列選項：

|選項|描述|
|------------|-----------------|
|**強制執行簽入使其僅包含屬於目前方案的檔案。**|只有在方案和專案的組態檔中指定的檔案，可以執行程式碼分析。 此原則可保證方案的一部分的所有程式碼會進行分析。|
|**強制執行 C /C++程式碼分析 (/analyze)**|需要所有的 C 或C++以建置專案 / analyze 編譯器選項，簽入之前執行程式碼分析。|
|**針對 Managed 程式碼強制執行程式碼分析**|需要所有的 managed 的專案執行程式碼分析，以及建置簽入之前。|

## <a name="to-specify-a-managed-rule-set"></a>若要指定受管理的規則設定

從**執行此規則集**清單中，使用下列方法之一：

- 選取 Microsoft 標準規則集。

- 選取 自訂規則集，即可 **\<選取規則集從原始檔控制...>** 。 然後，輸入原始檔控制瀏覽器中的規則集的版本控制路徑。 版本控制路徑的語法是：

   **$/** `TeamProjectName` **/** `VersionControlPath`

如需有關如何建立及實作自訂簽入原則規則集，請參閱[針對 Managed 程式碼的自訂實作簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)。

## <a name="see-also"></a>另請參閱

- [建立和使用程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)