---
title: 如何：指定要優先建置的目標 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28fa9137166c19a81aad2c75204400639916e472
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497022"
---
# <a name="how-to-specify-which-target-to-build-first"></a>如何：指定要優先建置的目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 指定要優先建置的目標](https://docs.microsoft.com/visualstudio/msbuild/how-to-specify-which-target-to-build-first)。  
  
  
專案檔可以包含一或多個 `Target` 項目來定義專案的建置方式。 除非專案檔內含 `DefaultTargets` 屬性、`InitialTargets` 屬性，或在命令列中使用 **/target** 參數來指定目標，否則 [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) 引擎會建置它找到的第一個專案以及任何相依性。  
  
## <a name="using-the-initialtargets-attribute"></a>使用 InitialTargets 屬性  
 `Project` 項目的 `InitialTargets` 屬性會指定優先執行的目標，即使已在命令列上或 `DefaultTargets` 屬性中指定目標也一樣。  
  
#### <a name="to-specify-one-initial-target"></a>指定一個初始目標  
  
-   在 `Project` 項目的 `InitialTargets` 屬性中，指定預設的目標。 例如:   
  
     `<Project InitialTargets="Clean">`  
  
 您可以在 `InitialTargets` 屬性中指定多個初始目標，方法是依序列出目標，然後使用分號來分隔每個目標。 清單中的目標將會循序執行。  
  
#### <a name="to-specify-more-than-one-initial-target"></a>指定多個初始目標  
  
-   在 `Project` 項目的 `InitialTargets` 屬性中，列出以分號分隔的初始目標。 例如，若要依序執行 `Clean` 目標和 `Compile` 目標，請輸入：  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>使用 DefaultTargets 屬性  
 如果未在命令列上明確指定目標，則 `Project` 項目的 `DefaultTargets` 屬性會指定要建置哪些目標。 如果已在 `InitialTargets` 和 `DefaultTargets` 屬性上指定目標，且未在命令列上指定目標，則 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會執行 `InitialTargets` 屬性中指定的目標，接著執行 `DefaultTargets` 屬性中指定的目標。  
  
#### <a name="to-specify-one-default-target"></a>指定一個預設目標  
  
-   在 `Project` 項目的 `DefaultTargets` 屬性中，指定預設的目標。 例如:   
  
     `<Project DefaultTargets="Compile">`  
  
 您可以在 `DefaultTargets` 屬性中指定多個預設目標，方法是依序列出目標，然後使用分號來分隔每個目標。 清單中的目標將會循序執行。  
  
#### <a name="to-specify-more-than-one-default-target"></a>指定多個預設目標  
  
-   在 `Project` 項目的 `DefaultTargets` 屬性中，列出以分號分隔的預設目標。 例如，若要依序執行 `Clean` 目標和 `Compile` 目標，請輸入：  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>使用 /target 參數  
 如果專案檔中未定義預設目標，或者，如果您不想使用預設目標，您可以使用命令列參數 **/target** 來指定不同的目標。 使用 **/target** 參數指定的目標即會執行，而不是執行 `DefaultTargets` 屬性所指定的目標。 `InitialTargets` 屬性中執行的目標永遠會先執行。  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>優先使用非預設的目標  
  
-   使用 **/target** 命令列參數，將目標指定為第一個目標。 例如:   
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>優先使用預設目標以外的數個目標  
  
-   使用 **/target** 命令列參數，列出以分號或逗號的目標。 例如:   
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>另請參閱
  [ MSBuild](msbuild.md)  
 [目標](../msbuild/msbuild-targets.md)   
 [如何：清除組建](../msbuild/how-to-clean-a-build.md)


