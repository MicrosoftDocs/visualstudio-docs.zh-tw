---
title: 如何：將專案設定成以平台為目標 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668195"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>如何：將專案設定成以平台為目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可讓您將應用程式的目標設定為不同的平台，包括 64 位元的平台。 如需 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中 64 位元平台支援的詳細資訊，請參閱 [64 位元應用程式](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)。

## <a name="targeting-platforms-with-the-configuration-manager"></a>利用組態管理員設定平台的目標
 [組態管理員]  可讓您快速加入新平台，以成為專案的目標。 如果您選取 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 隨附的其中一個平台，您的專案屬性會經過修改，以針對選取的平台建置專案。

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>將專案設定成以 64 位元平台為目標

1. 在功能表列上，選擇 [ **建置**]、[ **組態管理員**]。

2. 在 [使用中的方案平台]  清單中，選擇 64 位元平台作為方案的目標，然後選擇 [關閉]  按鈕。

   1. 如果您想要的平台未出現在 [使用中的方案平台]  清單中，請選擇 [新增]  。

        [新增方案平台]  對話方塊隨即出現。

   2. 在 [輸入或選取新平台]  清單中選擇 [x64]  。

       > [!NOTE]
       > 如果您將組態改為新的名稱，則必須在 [專案設計工具]  中修改設定，才能以正確的平台為目標。

   3. 如果您想要從目前的平台組態複製設定，請選擇所需項目，然後選擇 [確定]  按鈕。

   以 64 位元平台為目標的所有專案的屬性會進行更新，而專案的下一個組建會針對 64 位元平台進行最佳化。

## <a name="targeting-platforms-in-the-project-designer"></a>在專案設計工具中將平台設為目標
 專案設計工具也可供您將專案的目標設為不同的平台。 如果您在 [新增方案平台]  對話方塊清單中，選取了一個不適用於方案的平台，您可以建立自訂組態名稱並修改 [專案設計工具]  中的設定，以正確的平台為目標。

 根據您所使用的程式設計語言而定，此工作的執行會有所不同。 請參閱下列連結以取得詳細資訊：

- 若是 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 專案，請參閱 [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1)。

- 若是 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 專案，請參閱[專案設計工具、建置頁 (C#)](../ide/reference/build-page-project-designer-csharp.md)。

- 若是 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 專案，請參閱 [/clr (Common Language Runtime 編譯)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c)。

## <a name="see-also"></a>另請參閱
 [瞭解組建平臺](../ide/understanding-build-platforms.md) [/Platform （C#編譯器選項）](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64 位應用程式](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Visual Studio IDE 64 位支援](../ide/visual-studio-ide-64-bit-support.md)
