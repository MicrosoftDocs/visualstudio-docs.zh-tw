---
title: 選項對話方塊、環境、國際設定
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1609f33230942c2f5d026eb072e3e85860137d4b
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143147"
---
# <a name="international-settings-environment-options-dialog-box"></a>選項對話方塊、環境、國際設定

當您在電腦上安裝多個語言版本的整合式開發環境 (IDE) 時，[國際設定] 頁面可讓您變更預設語言。 您可以從 [工具] 功能表選取 [選項]，然後從 [環境] 資料夾選擇 [國際設定]，來存取這個對話方塊。 如果此頁面未出現在清單中，請在 [選項] 對話方塊中選取 [顯示所有設定]。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

 **語言**：列出已安裝產品語言版本的可用語言。 除非您在電腦上安裝多個語言版本，否則無法使用這個選項。 如果產品的多個語言或產品的混合語言安裝共用環境，這個 [語言] 區段會變更為 [與 Microsoft Windows 相同]。

> [!CAUTION]
> 在安裝了多個語言的系統中，Visual C++ 建置工具 (cl.exe、link.exe、nmake.exe、bscmake.exe 和相關檔案) 不會受到這項設定的影響。 這些工具會使用最後一個安裝之語言的版本。 因為 Visual C++ 建置工具不會使用附屬 DLL 模型，所以會覆寫先前已安裝語言的建置工具。

## <a name="see-also"></a>請參閱

- [安裝語言套件](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)