---
title: 編譯和建置
description: 本文描述如何在 Visual Studio for Mac 中編譯和建置專案與方案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: d5613a47785f1bb3fbb2a56f8458bba1946930e7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719797"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中編譯和建置

Visual Studio for Mac 可用來在專案開發期間建置應用程式和建立組件。 請務必及早且經常編譯和建置您的程式碼，讓您能夠識別類型不符以及其他的編譯時期錯誤。

## <a name="building-from-the-ide"></a>從 IDE 建置

使用 Visual Studio for Mac 可讓您立即建立和執行組建，同時仍然能夠控制組建功能。 Visual Studio for Mac 會使用 MSBuild 作為基礎建置系統。

在 IDE 中建立的所有專案和方案都會有預設的組建組態，以定義組建的內容。 您可以編輯這些組態，也可以建立自己的組態。 建立或修改這些組態會自動更新專案檔，MSBuild 之後會使用該檔案來建置專案。

如需如何在 IDE 中建立專案和方案的詳細資訊，請參閱[建置和清除專案與方案](building-and-cleaning-projects-and-solutions.md)指南。

Visual Studio for Mac 也可用來執行下列作業：

* 變更輸出路徑。 這是在您的專案選項中進行編輯：

    ![變更輸出路徑](media/compiling-and-building-image4.png)

* 變更組建輸出的詳細資訊：

    ![變更組建的詳細資訊](media/compiling-and-building-image5.png)

* 在建置或清除之前、期間或之後加入自訂命令：

    ![新增自訂命令](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>從命令列建置

您可以使用 MSBuild 組建引擎，透過命令列建置應用程式。

如需使用 MSBuild 的詳細資訊，請參閱 [MSBuild](/visualstudio/msbuild/msbuild) 內容。

## <a name="building-from-azure-pipelines"></a>從 Azure Pipelines 建置

* [打造您的 Xamarin 應用程式](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [使用 Xamarin 的連續整合](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>另請參閱

- [編譯與建置 (Windows 上的 Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)