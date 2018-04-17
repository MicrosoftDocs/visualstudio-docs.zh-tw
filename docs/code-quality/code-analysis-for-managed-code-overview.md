---
title: 程式碼分析在 Visual Studio 中的 managed 程式碼 |Microsoft 文件
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6d654cb3a7f0d0e952b447337603718c20eaee3e
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Managed 程式碼的程式碼分析概觀

Visual Studio 2017 分析 managed 程式碼有兩種： 與舊版*FxCop*靜態分析 managed 組件，並使用.NET 編譯器平台*分析器*。 本主題涵蓋 FxCop 靜態程式碼分析。 若要了解有關使用.NET 編譯器平台分析器來分析程式碼的詳細資訊，請參閱[概觀的 Roslyn 分析器](../code-quality/roslyn-analyzers-overview.md)。

Managed 程式碼的程式碼分析可以分析 Managed 組件並回報有關組件的資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。

分析工具會將分析期間所做的檢查顯示為警告訊息。 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。

## <a name="ide-integrated-development-environment-integration"></a>IDE （整合式的開發環境） 整合

您可以手動或自動執行您的專案程式碼分析。

若要建立專案時，您每次執行程式碼分析，選取**建置時啟用程式碼分析**專案屬性頁上。 如需詳細資訊，請參閱[How to： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

若要手動執行程式碼分析的專案上，從功能表列選擇**分析** > **執行程式碼分析** > **上執行程式碼分析\<專案>**。

## <a name="rule-sets"></a>規則集

Managed 程式碼的程式碼分析規則分組為[規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)。 您可以使用其中一個 Microsoft 標準規則集，或您可以[建立自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)來滿足特定需求。

## <a name="suppress-warnings"></a>隱藏警告

最大的用途是指出某個警告不適用。 這會通知程式開發人員和其他稍後可能會檢閱程式碼的人員，指出您已經調查此警告並且隱藏或忽略它。

在原始程式檔的警告的隱藏項目是透過自訂屬性來實作。 若要隱藏警告，請將 `SuppressMessage` 屬性加入至原始程式碼，如下列範例所示：

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

如需詳細資訊，請參閱[隱藏的警告，](../code-quality/in-source-suppression-overview.md)。

> [!NOTE]
> 如果您將專案移轉至 Visual Studio 2017 時，可能會突然面臨著大量的程式碼分析警告。 如果您不可以修正警告，而且想要立即上手，您可以*基準*分析狀態，您的專案。 從**分析**功能表上，選取**執行程式碼分析並隱藏作用中問題**。

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>執行程式碼分析做為簽入原則的一部分

從組織的角度來看，您可能想指定所有的簽入都要滿足特定的原則， 尤其您會想要確認您已經確實遵循這些原則：

- 正在簽入程式碼中有任何建置錯誤。

- 執行程式碼分析做為最新組建的一部分。

您可以指定簽入原則，達成上述要求。 如需詳細資訊，請參閱[使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)。

## <a name="team-build-integration"></a>Team build 整合

您可以使用建置系統的整合式功能，執行分析工具做為建置流程的一部分。 如需詳細資訊，請參閱[組建與版本 (VSTS)](/vsts/build-release/index)。

## <a name="see-also"></a>另請參閱

- [Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [如何： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
