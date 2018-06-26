---
title: 客戶經驗改進計畫
description: 了解如何管理 Visual Studio 中的隱私權設定。
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dbc83a2d3fe1b2f5bb32a6baaf336c0a6c46e7d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572630"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio 客戶經驗改進計畫

Visual Studio 客戶經驗改進計畫 (VSCEIP) 是設計來協助 Microsoft 隨著時間改善 Visual Studio。 此計畫會[收集有關錯誤](../ide/diagnostic-data-collection.md)、電腦硬體以及使用者如何使用 Visual Studio 的資訊，而不會中斷使用者在電腦上的工作。 所收集的資訊可協助 Microsoft 找出應改善的功能。 本文討論如何選擇加入或退出 VSCEIP。

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>選擇加入或退出

VSCEIP 預設為開啟。 您可以遵循下列指示將它關閉，或重新開啟：

1. 啟動 Visual Studio。

1. 從 [協助] 功能表上，指向 [傳送意見反應]，然後選取 [設定]。

   [Visual Studio 經驗改進計畫] 對話方塊隨即開啟。

1. 若要選擇退出，請選取 [否，我不願意參與]，然後選取 [確定]。
   若要選擇加入，請選取 [是，我願意參與]，然後選取 [確定]。

   ![[Visual Studio 經驗改進計畫] 對話方塊](media/experience-improvement-program.png)

### <a name="registry-settings"></a>登錄設定

如果您安裝 [Build Tools for Visual Studio](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017)，您必須更新登錄以設定 VSCEIP。 企業客戶可建構群組原則，透過設定以登錄為基礎原則的方式，選擇加入或退出 VSCEIP。

相關的登錄機碼與設定如下：

在 64 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**  
在 32 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**  
啟用群組原則時，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  

項目 = **OptIn**

值 = (DWORD)
- **0** 是選擇退出 (關閉 VSCEIP)
- **0** 是選擇加入 (開啟 VSCEIP)

> [!CAUTION]
> 不當編輯登錄可能會對系統造成嚴重損害。 在變更登錄前，您應先備份電腦上任何重要的資料。 如果　您在套用手動變更之後遇到問題，也可以使用 [上次的正確設定] 啟動選項。

如需 VSCEIP 收集、處理或傳輸之資訊的詳細資訊，請參閱 [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)。

## <a name="see-also"></a>另請參閱

* [Visual Studio 所收集的診斷資訊](diagnostic-data-collection.md)
* [告訴我們](../ide/talk-to-us.md)
* [如何回報 Visual Studio 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)
* [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)
