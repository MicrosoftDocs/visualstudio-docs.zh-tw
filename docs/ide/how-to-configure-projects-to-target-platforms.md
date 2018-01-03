---
title: "如何：將專案設定成以平台為目標 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ccca87721c39daa7e613d7426c9d5fed6a144cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-projects-to-target-platforms"></a>如何：將專案設定成以平台為目標
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可讓您將應用程式的目標設定為不同的平台，包括 64 位元的平台。 如需 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中 64 位元平台支援的詳細資訊，請參閱 [64 位元應用程式](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)。  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>利用組態管理員設定平台的目標  
 [組態管理員] 可讓您快速加入新平台，以成為專案的目標。 如果您選取 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 隨附的其中一個平台，您的專案屬性會經過修改，以針對選取的平台建置專案。  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>將專案設定成以 64 位元平台為目標  
  
1.  在功能表列上，選擇 [ **建置**]、[ **組態管理員**]。  
  
2.  在 [使用中的方案平台] 清單中，選擇 64 位元平台作為方案的目標，然後選擇 [關閉] 按鈕。  
  
    1.  如果您想要的平台未出現在 [使用中的方案平台] 清單中，請選擇 [新增]。  
  
         [新增方案平台] 對話方塊隨即出現。  
  
    2.  在 [輸入或選取新平台] 清單中選擇 [x64]。  
  
        > [!NOTE]
        >  如果您將組態改為新的名稱，則必須在 [專案設計工具] 中修改設定，才能以正確的平台為目標。  
  
    3.  如果您想要從目前的平台組態複製設定，請選擇所需項目，然後選擇 [確定] 按鈕。  
  
 以 64 位元平台為目標的所有專案的屬性會進行更新，而專案的下一個組建會針對 64 位元平台進行最佳化。  
  
## <a name="targeting-platforms-in-the-project-designer"></a>在專案設計工具中將平台設為目標  
 專案設計工具也可供您將專案的目標設為不同的平台。 如果您在 [新增方案平台] 對話方塊清單中，選取了一個不適用於方案的平台，您可以建立自訂組態名稱並修改 [專案設計工具] 中的設定，以正確的平台為目標。  
  
 根據您所使用的程式設計語言而定，此工作的執行會有所不同。 請參閱下列連結以取得詳細資訊：  
  
-   若是 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案，請參閱 [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)。  
  
-   若是 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案，請參閱[專案設計工具、建置頁 (C#)](../ide/reference/build-page-project-designer-csharp.md)。  
  
-   若是 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案，請參閱 [/clr (Common Language Runtime 編譯)](/cpp/build/reference/clr-common-language-runtime-compilation)。  
  
## <a name="see-also"></a>請參閱  
 [了解組建平台](../ide/understanding-build-platforms.md)   
 [/platform (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64 位元應用程式](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio IDE 64 位元支援](../ide/visual-studio-ide-64-bit-support.md)