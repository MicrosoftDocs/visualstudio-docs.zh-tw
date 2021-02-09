---
title: 選項對話方塊中的國際設定
description: 瞭解當您安裝多個語言版本的 IDE 時，如何使用 [環境] 區段中的 [國際設定] 頁面來變更預設語言。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9dc19c69bf99ba6f66648f396468ff36444eb3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852267"
---
# <a name="options-dialog-box-environment--international-settings"></a>選項對話方塊：環境 \> 國際設定

當您在電腦上安裝多個語言版本的整合式開發環境 (IDE) 時，[國際設定] 頁面可讓您變更預設語言。 您可以從 [工具] 功能表選取 [選項]，然後從 [環境] 資料夾選擇 [國際設定]，來存取這個對話方塊。

**Language**

列出已安裝產品語言版本的可用語言。 如果產品的多個語言或產品的混合語言安裝共用環境，這個 [語言] 區段會變更為 [與 Microsoft Windows 相同]。

> [!CAUTION]
> 在安裝了多個語言的系統中，Visual C++ 建置工具 (cl.exe、link.exe、nmake.exe、bscmake.exe 和相關檔案) 不會受到這項設定的影響。 這些工具會使用最後一個安裝之語言的版本。 因為 Visual C++ 建置工具不會使用附屬 DLL 模型，所以會覆寫先前已安裝語言的建置工具。

### <a name="see-also"></a>另請參閱

- [安裝語言套件](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
