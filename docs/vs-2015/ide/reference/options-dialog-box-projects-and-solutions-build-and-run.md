---
title: 選項對話方塊、專案和解決方案、建置並執行 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655180"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>選項對話方塊, 專案和方案, 建置和執行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在此對話方塊中，您可以指定可同時建置的 Visual C++ 或 Visual C# 專案最大數目、特定的預設建置行為，和一些建置記錄檔設定。 若要開啟 [選項] 對話方塊，請在功能表列上選擇 [工具]、[選項]。 若要存取這組選項，請展開 [專案和方案]，然後選擇 [建置並執行]。

## <a name="uielement-list"></a>UIElement 清單
 **平行專案組建的最大數目**指定可以同時建立的視覺C++效果和C#視覺效果專案的最大數目。 若要最佳化建置程序，平行專案組建的最大數目會自動設定為您電腦的 CPU 數目。 最大值是 32。

 **只在執行時建立啟始專案和**相依性當您選擇 F5 鍵時，如果選取此核取方塊，則只會建立啟始專案和其相依性;從功能表列選擇 [ **Debug**]、[ **Start** ];或選擇功能表列上的 [**組建**]、[**建立**]。 當您選擇 F5 鍵；選擇功能表列上的 [偵錯]、[開始]，或選擇功能表列上的 [建置]、[建置] 時，如果清除此核取方塊，則會建置所有專案、相依性和解決方案。 預設會清除這個選項。

 **執行時 (當專案過期時)**
 > [!NOTE]
> 此清單只適用於 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案。

 當您選擇 F5 鍵或選擇功能表列上的 [偵錯]、[開始] 時，如果專案設定已過期，則預設會出現一則訊息。 您可以指定是否依然要建置專案，以及是否顯示此訊息。 使用此選項來指定是否顯示訊息，以及建置行為在不顯示訊息時應該為何。

 **一律建立**訊息方塊不會出現，而且即使過期設定，也會建立專案。 當您在訊息中選取 [不要再顯示此對話方塊] 方塊，然後選擇 [是] 按鈕時，即設定此選項。

 **永不建立**訊息方塊不會出現，而且不會建立專案。 當您在訊息中選取 [不要再顯示此對話方塊] 方塊，然後選擇 [否] 按鈕時，即設定此選項。

 **提示建立**每次專案設定已過期時，就會顯示訊息方塊。

 執行**時，發生組建或部署錯誤時**當您從 [**組建**] 功能表啟動組建時，如果發生組建錯誤，則會出現一則訊息。 您可以指定是否要繼續啟動應用程式，以及每次發生建置錯誤時是否顯示訊息。 使用此選項來指定是否顯示訊息，以及行為在不顯示訊息時應該為何。

> [!NOTE]
> 此選項只適用於 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案。

 **提示啟動**每次發生組建錯誤時，就會顯示訊息方塊。

 不**啟動**訊息方塊不會出現，而且應用程式也不會啟動。 當您在訊息方塊中選取 [不要再顯示此對話方塊] 核取方塊，然後選擇 [否] 按鈕時，即設定此選項。

 **啟動舊版本**訊息方塊不會出現，而且新建立的應用程式版本也不會啟動。 當您在訊息方塊中選取 [不要再顯示此對話方塊] 核取方塊，然後選擇 [是] 按鈕時，即設定此選項。

 **針對新的方案，使用目前選取的專案做為啟始專案**如果選取此核取方塊，新的方案會使用目前選取的專案做為啟始專案。

 **MSBuild 專案組建輸出詳細**資訊決定要在組建的 [**輸出**] 視窗中顯示多少資訊。

 **MSBuild 專案組建記錄檔詳細資訊**
 > [!NOTE]
> 此選項只適用於 Visual C++ 專案。

 決定多少資訊會寫入建置記錄檔，其位置在 \\...\\*專案名稱*\Debug\\*專案名稱*.log。

## <a name="see-also"></a>請參閱
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)
