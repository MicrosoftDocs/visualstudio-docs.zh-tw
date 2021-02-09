---
title: 如何：指定要優先建置的目標 | Microsoft Docs
description: 瞭解如何在 MSBuild 專案檔中，指定要先建立的初始目標或預設目標。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f41c9fec5b5ce9b6e4716c83edf9cd9f43e0eb94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914213"
---
# <a name="how-to-specify-which-target-to-build-first"></a>如何：指定要優先建置的目標

專案檔可以包含一或多個 `Target` 項目來定義專案的建置方式。 Microsoft Build Engine (MSBuild) 引擎會建立它所找到的第一個目標，以及任何相依性，除非專案檔包含 `DefaultTargets` 屬性、 `InitialTargets` 屬性或目標是在命令列使用 **-target** 參數指定的。
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

 如果未在命令列上明確指定目標，則 `Project` 項目的 `DefaultTargets` 屬性會指定要建置哪些目標。 如果在和屬性中指定了目標， `InitialTargets` `DefaultTargets` 但在命令列上未指定任何目標，則 MSBuild 會執行屬性中指定的目標， `InitialTargets` 後面接著屬性中指定的目標 `DefaultTargets` 。

#### <a name="to-specify-one-default-target"></a>指定一個預設目標

- 在 `Project` 項目的 `DefaultTargets` 屬性中，指定預設的目標。 例如：

   `<Project DefaultTargets="Compile">`

  您可以在 `DefaultTargets` 屬性中指定多個預設目標，方法是依序列出目標，然後使用分號來分隔每個目標。 清單中的目標將會循序執行。

#### <a name="to-specify-more-than-one-default-target"></a>指定多個預設目標

- 在 `Project` 項目的 `DefaultTargets` 屬性中，列出以分號分隔的預設目標。 例如，若要依序執行 `Clean` 目標和 `Compile` 目標，請輸入：

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>使用 -target 參數

 如果專案檔中未定義預設目標，或者，如果您不想使用預設目標，您可以使用命令列參數 **-目標** 來指定不同的目標。 使用 **-target** 參數指定的目標或目標會執行，而不是屬性所指定的目標 `DefaultTargets` 。 `InitialTargets` 屬性中執行的目標永遠會先執行。

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>優先使用非預設的目標

- 使用 **-target** 命令列參數，將目標指定為第一個目標。 例如：

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>優先使用預設目標以外的數個目標

- 使用 **-target** 命令列參數，列出以分號或逗號分隔的目標。 例如：

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [目標](../msbuild/msbuild-targets.md)
- [如何：清除組建](../msbuild/how-to-clean-a-build.md)
