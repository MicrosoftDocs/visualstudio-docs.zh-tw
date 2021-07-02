---
title: Visual Studio 中的連線體驗
description: 連線體驗會從用戶端電腦連線到網際網路，並為客戶提供服務。
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222886"
---
# <a name="connected-experiences-in-visual-studio"></a>**Visual Studio 中的連線體驗** #

Visual Studio 是由用戶端軟體應用程式和連線體驗所組成，其設計目的是讓您更有效率地撰寫程式碼。 更新[NuGet](/nuget/consume-packages/install-use-packages-visual-studio)套件、選取[IntelliCode](/visualstudio/intellicode/overview)建議，以及透過[Live Share](/visualstudio/liveshare/quickstart/share)與其他開發人員共同作業，都是連線體驗的範例。 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>選擇這些連線體驗是否可供使用 ##

您可以選擇要使用的連線體驗。 使用特定的連線體驗時，必須合約為 Visual Studio EULA 的不同條款和其他條款。 這些體驗可能是 Microsoft 擁有的線上服務及/或協力廠商所擁有的服務。 例如，當您使用 GitHub 連線體驗時，將適用[GitHub 隱私權聲明](https://docs.github.com/github/site-policy/github-privacy-statement)和[GitHub 的服務](https://docs.github.com/github/site-policy/github-terms-of-service)條款、 [GitHub 公司的服務條款](https://docs.github.com/github/site-policy/github-corporate-terms-of-service)及/或[其他產品條款](https://docs.github.com/github/site-policy/github-additional-product-terms)。 如果您回報 [問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)，即表示您同意 [Microsoft 使用條款](https://www.microsoft.com/legal/terms-of-use) 及 [microsoft 隱私權聲明](https://privacy.microsoft.com/en-us/privacystatement)。 如果您使用 NuGet 服務，即表示您同意[使用 NuGet 使用條款](https://www.nuget.org/policies/Terms)和[Microsoft 隱私權聲明](https://privacy.microsoft.com/en-us/privacystatement)。 

當您安裝 Visual Studio 時，[您可以選擇性地選取要安裝的工作負載和元件](/visualstudio/install/install-visual-studio)。 工作負載和元件可以利用協力廠商軟體，而且它們可能會根據其功能來啟用連線體驗。 例如， [下載 azure 開發工作負載可讓您將雲端應用程式發佈至 azure](https://visualstudio.microsoft.com/vs/features/azure/)。 根據您的安裝選項，您也可以使用 [工具] 和 [選項] 功能表來連接、設定及使用連線體驗。 例如，您可以連接到伺服器、新增 Azure 服務驗證，或變更 IntelliCode 或 LiveShare 設定。  

您也可以使用組織的 [防火牆設定](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) 來啟用或停用服務的連接。 請注意，停用端點的連接可能會對相關 Visual Studio 功能的效能造成負面影響或停用。 

最後，Visual Studio Marketplace 提供的擴充功能可能會啟用第一方或協力廠商連線體驗。 Visual Studiomarketplace 受[Visual Studio marketplace 使用](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf)規定和[Microsoft 隱私權聲明](https://privacy.microsoft.com/en-us/privacystatement)的約束。 每個擴充功能都需要與該供應專案相關的特定使用規定與隱私權聲明的合約。  


## <a name="required-service-data"></a>必要的服務資料 ##

必要的服務資料可能包含連接體驗作業的相關資訊，這些資訊可讓基礎服務保持安全、最新狀態，並如預期般執行。 如果您選擇使用可分析內容的連線體驗（例如 IntelliCode），則也會傳送並處理您為模型選取的程式碼，以提供您連線的體驗。 必要的服務資料也可以包含連接體驗執行其工作所需的資訊，例如更新 NuGet 套件。 您可以選擇是否要使用特定服務，以管理所需的服務資料。 如果您未使用服務，則不會收集任何必要的服務資料。 

必要的服務資料與診斷資料不同，因為診斷資料與您裝置上執行的軟體相關。 您選擇是否要參與[Visual Studio 客戶經驗改進計畫 (VSCEIP) 控制診斷資料的隱私權設定](/visualstudio/ide/visual-studio-experience-improvement-program)，但此設定不會影響是否傳送所需的服務資料。 

## <a name="diagnostic-data-collection"></a>診斷資料收集 ##

診斷資料可用來維持 Visual Studio 的安全和最新狀態、偵測、診斷和修正問題，也會改善產品。 診斷資料會收集並傳送給 Microsoft，Visual Studio 用戶端軟體在使用者的裝置上執行。

當您退出宣告時，您會退出宣告選擇性的診斷資料收集。 需要進行某些診斷資料收集，以確定 Visual Studio 安全、最新狀態，並如預期般執行。 必要的診斷資料收集將不會受到您退出宣告 [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program)的影響。 
