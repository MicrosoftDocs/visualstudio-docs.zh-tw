---
title: 設計 Windows Forms 應用程式
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8280a60f1d265336d427079bdef6612b42ed4330
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68981634"
---
# <a name="windows-forms-designer-overview"></a>Windows Form 設計工具概觀

Visual Studio 中的 Windows Form 設計工具能針對建立以 Windows Forms 為基礎的應用程式提供快速的開發解決方案。 Windows Form 設計工具可以讓您輕鬆地將控制項加入表單，排列它們，然後撰寫其事件的程式碼。 如需 Windows Forms 的詳細資訊，請參閱 [Windows Forms 概觀](/dotnet/framework/winforms/windows-forms-overview)。

## <a name="functionality"></a>功能

透過使用設計工具，您可以：

- 將元件、資料控制項，或是以 Windows 為基礎的控制項新增到表單上。

- 在設計工具中按兩下表單並撰寫該表單之 `Load` 事件的程式碼，或是按兩下表單上的控制項並撰寫該控制項預設事件的程式碼。

- 選取控制項來編輯該控制項的 Text 屬性並輸入名稱。

- 使用滑鼠或方向鍵來移動控制項，來調整所選取之控制項的位置。 同樣地，使用 Ctrl 和方向鍵來更精確地調整位置。 最後，使用 Shift 和方向鍵來調整控制項的大小。

- 在按一下時選取 **Shift** 或 **Ctrl** 來選取多個控制項。 使用 **Shift**+按一下時，所選取的第一個控制項將會是對齊或調整大小時的主要控制項。 使用 **Ctrl**+按一下時，最後選取的控制項將會是主要控制項，因此主要控制項會隨著新增控制項而變更。 或者，您也可以拖曳選取矩形來涵蓋您想要選取的控制項，以選取多個控制項。

> [!NOTE]
> 使用 Windows Form 設計工具 (而非資源編輯器) 來變更表單的資源 ( *.resx*) 檔案。 如果您編輯以表單為基礎的 .resx 檔案，您將會看見警告，表示您在資源編輯器中所做的變更可能會遺失。 這是因為該 .resx 檔案是由 Windows Form 設計工具產生。

## <a name="see-also"></a>另請參閱

- [Windows Form 概觀](/dotnet/framework/winforms/windows-forms-overview)
- [Windows Forms 控制項](/dotnet/framework/winforms/controls/)
- [適用於 Windows Forms 控制項的協助工具](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Windows Forms 中的使用者輸入](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Windows Forms 中的資料繫結](/dotnet/framework/winforms/windows-forms-data-binding)
- [增強 Windows Forms 應用程式](/dotnet/framework/winforms/advanced/)