---
title: 如何：指定要優先建置的目標 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7656237be5cf7906293a294885cfa3e6c8bd4e36
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072524"
---
# <a name="how-to-specify-which-target-to-build-first"></a>如何：指定要優先建置的目標

專案檔可以包含一或多個 `Target` 項目來定義專案的建置方式。 Microsoft Build Engine (MSBuild) 引擎產生它找到的第一個目標和任何依賴項,`DefaultTargets`除非專案`InitialTargets`檔包含 屬性、 屬性或目標,使用 **-target**開關在命令列中指定。
## <a name="use-the-initialtargets-attribute"></a>使用 InitialTargets 屬性

`Project` 項目的 `InitialTargets` 屬性會指定優先執行的目標，即使已在命令列上或 `DefaultTargets` 屬性中指定目標也一樣。

#### <a name="to-specify-one-initial-target"></a>指定一個初始目標

- 在 `Project` 項目的 `InitialTargets` 屬性中，指定預設的目標。 例如：

   `<Project InitialTargets="Clean">`

  您可以在 `InitialTargets` 屬性中指定多個初始目標，方法是依序列出目標，然後使用分號來分隔每個目標。 清單中的目標將會循序執行。

#### <a name="to-specify-more-than-one-initial-target"></a>指定多個初始目標

- 在 `Project` 項目的 `InitialTargets` 屬性中，列出以分號分隔的初始目標。 例如，若要依序執行 `Clean` 目標和 `Compile` 目標，請輸入：

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>使用 DefaultTargets 屬性

 如果未在命令列上明確指定目標，則 `Project` 項目的 `DefaultTargets` 屬性會指定要建置哪些目標。 如果在`InitialTargets`和`DefaultTargets`屬性中指定目標,並且命令列上未指定目標,則 MSBuild 運行屬性`InitialTargets`中指定的目標`DefaultTargets`,後跟 屬性中指定的目標。

#### <a name="to-specify-one-default-target"></a>指定一個預設目標

- 在 `Project` 項目的 `DefaultTargets` 屬性中，指定預設的目標。 例如：

   `<Project DefaultTargets="Compile">`

  您可以在 `DefaultTargets` 屬性中指定多個預設目標，方法是依序列出目標，然後使用分號來分隔每個目標。 清單中的目標將會循序執行。

#### <a name="to-specify-more-than-one-default-target"></a>指定多個預設目標

- 在 `Project` 項目的 `DefaultTargets` 屬性中，列出以分號分隔的預設目標。 例如，若要依序執行 `Clean` 目標和 `Compile` 目標，請輸入：

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>使用 -target 參數

 如果在專案檔中未定義預設目標,或者不想使用該預設目標,則可以使用命令行開關 **-目標**來指定其他目標。 使用 **-target**開關指定的目標或目標將運行`DefaultTargets`,而不是屬性指定的目標。 `InitialTargets` 屬性中執行的目標永遠會先執行。

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>優先使用非預設的目標

- 使用 **-目標**命令列開關將目標指定為第一個目標。 例如：

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>優先使用預設目標以外的數個目標

- 使用 **-目標**命令列開關列出以分號或逗號分隔的目標。 例如：

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [目標](../msbuild/msbuild-targets.md)
- [如何:清理產生](../msbuild/how-to-clean-a-build.md)
