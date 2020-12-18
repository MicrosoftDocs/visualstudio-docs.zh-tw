---
title: 客戶經驗改進計畫
description: 了解如何管理 Visual Studio 中的隱私權設定。
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eae7e4726f720b1c9974682525bbe2a28ee38d5f
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97667932"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio 客戶經驗改進計畫

Visual Studio 客戶經驗改進計畫 (VSCEIP) 是設計來協助 Microsoft 隨著時間改善 Visual Studio。 此計畫會[收集有關錯誤](../ide/diagnostic-data-collection.md)、電腦硬體以及使用者如何使用 Visual Studio 的資訊，而不會中斷使用者在電腦上的工作。 所收集的資訊可協助 Microsoft 找出應改善的功能。 本文討論如何選擇加入或退出 VSCEIP。

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEIP 遙測加入宣告或退出設定不會套用至 Visual Studio 中的 [回報問題]。 當您回報問題記錄檔時，只有在您按一下 [提交] 來提供許可權時，才會收集並傳送給 Microsoft。 如果您想要在提交至「回報問題」之前記錄管理，請參閱 [意見反應資料隱私權](./developer-community-privacy.md) 以取得詳細資料。

## <a name="opt-in-or-out"></a>選擇加入或退出

VSCEIP 預設為開啟。 您可以遵循下列指示將它關閉，或重新開啟：

1. 在 Visual Studio 中，**選擇 [說明**  >  **傳送意見**]，然後選取 [**設定**]。

   [Visual Studio 經驗改進計畫] 對話方塊隨即開啟。

1. 若要選擇退出，請選取 [否，我不願意參與]，然後選取 [確定]。 若要選擇加入，請選取 [是，我願意參與]，然後選取 [確定]。

   ![[Visual Studio 經驗改進計畫] 對話方塊](media/experience-improvement-program.png)

### <a name="registry-settings"></a>登錄設定

如果您安裝 [Build Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)，您必須更新登錄以設定 VSCEIP。 企業客戶可建構群組原則，透過設定以登錄為基礎原則的方式，選擇加入或退出 VSCEIP。

相關的登錄機碼與設定如下：

::: moniker range="vs-2017"

- 在 64 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- 在 32 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- 當群組原則啟用時，機碼 = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- 在 64 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- 在 32 位元作業系統上，機碼 = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- 當群組原則啟用時，機碼 = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entry = **OptIn**

Value = (DWORD)

- **0** 是退出宣告 (關閉 VSCEIP) 
- **1** 是選擇 (開啟 VSCEIP) 

> [!CAUTION]
> 不正確地編輯登錄可能會對系統造成嚴重的損害。 變更登錄之前，您應該先備份電腦所有的重要資料。 如果您在套用手動變更之後遇到問題，也可以使用 [ **上次** 的正確設定] 啟動選項。

如需 VSCEIP 收集、處理或傳輸之資訊的詳細資訊，請參閱 [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)。

## <a name="see-also"></a>另請參閱

* [Visual Studio 所收集的診斷資訊](diagnostic-data-collection.md)
* [Visual Studio 意見反應選項](../ide/feedback-options.md)
* [如何回報 Visual Studio 的問題](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)
* [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)
