---
title: 視覺工作室的 UX 要點 |微軟文件
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698336"
---
# <a name="ux-essentials-for-visual-studio"></a>適用於 Visual Studio 的 UX 基本項目

## <a name="best-practices"></a>最佳作法

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. 在視覺工作室環境中保持一致。

- 遵循 shell 中現有的[互動模式](interaction-patterns-for-visual-studio.md)。

- 設計特點與外殼的視覺語言和[工藝要求](evaluation-tools-for-visual-studio.md)一致。

- 當共用命令和控件存在時,請使用它們。

- 瞭解 Visual Studio 層次結構及其如何建立上下文並推動 UI。

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. 對字體和顏色使用環境服務。

- UI 應尊重當前[環境字體](fonts-and-formatting-for-visual-studio.md)設置,除非在"選項"對話方塊中的"字型和顏色"頁中公開該設置以進行自定義。

- UI 元素必須使用[VSColor 服務](colors-and-styling-for-visual-studio.md),使用共用環境權杖或特定於功能的權杖。

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. 使所有影像與新 VS 樣式保持一致。

- 遵循圖示、字形和其他圖形的可視化工作室設計原則。

- 不要將文字放在圖形元素中。

### <a name="4-design-from-a-user-centric-perspective"></a>4. 從以使用者為中心的角度進行設計。

- 在任務流之前創建任務流。

- 熟悉您的使用者,並在您的規範中明確瞭解這些知識。

- 查看 UI 時,請評估完整的體驗以及詳細資訊。

- 設計 UI,使其無論區域設置或語言如何,都能保持功能性和吸引力。

## <a name="screen-resolution"></a>螢幕解析度

### <a name="minimum-resolution"></a>最低解析度

- Visual Studio 2015 的最低解析度為**1280x720**。 這意味著可以在此解析度*possible*下 使用 Visual Studio,儘管它可能不是最佳的用戶體驗。 不能保證所有方面都可用於低於 1280x720 的解析度。

- 視覺工作室的目標解析度為**1366x768。** 這是我們承諾*獲得良好*用戶體驗的最低解析度。

- 初始對話框高度應**小於 700 像素**,因此適合在 96 dpi 處的 IDE 幀的最小解析度。

### <a name="high-density-displays"></a>高密度顯示器
 可視化工作室中的 UI 必須在 Windows 支援開箱即用的所有 DPI 縮放因素中很好地工作:150%、200% 和 250%。

## <a name="anti-patterns"></a>反模式
 Visual Studio 包含許多遵循我們指南和最佳實務的 UI 範例。 為了保持一致,開發人員通常借用與構建的產品 UI 設計模式類似的產品 UI 設計模式。 儘管這是一種幫助我們在使用者交互和可視化設計中保持一致性的好方法,但由於進度限制或缺陷優先順序,我們偶爾會提供一些不符合我們準則的詳細資訊。 在這些情況下,我們不希望團隊複製這些"反模式"之一,因為它們在 Visual Studio 環境中激增了壞或不一致的 UI。

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>預設使用錯誤狀態顯示所需的欄位/設定

#### <a name="feature-team-goals"></a>功能團隊目標

- 警告使用者他們已添加必須配置的元素。

- 將使用者的注意力吸引到需要輸入的區域。

#### <a name="anti-pattern-solution"></a>反模式解決方案
 使用者一旦啟動操作並在完成任務之前,立即將關鍵停止圖示放在需要配置的區域旁邊。

#### <a name="example-manifest-designer-declarations"></a>範例:清單設計器聲明
 加入聲明會立即將其置於錯誤狀態,該狀態將一直持續到使用者設置所需的屬性。

 在這種情況下,還有一個額外的問題,因為用於警報的圖示包含一個""&times;圖示,因此不能使用常見的刪除圖示。 因此,UI 使用"刪除"按鈕,這是一個更笨重的控制項。

 ![預設情況下,將 UI 置於錯誤狀態是可視化工作室反模式。](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "清單設計錯誤宣告反模式")<br />預設情況下,將 UI 置於錯誤狀態是可視化工作室反模式。

#### <a name="alternatives"></a>替代方案

解決這個問題的更好解決方案是:

- 允許使用者添加聲明而不發出警告,然後立即移動以設置項上的屬性。

- 當焦點從項目移動時添加警告圖示(金三角形),例如向清單中添加其他聲明或嘗試更改設計器中的選項卡。

- 如果用戶嘗試在任何聲明上設置屬性之前更改選項卡,請彈出一個對話框,解釋在警告解決之前,應用程式不會生成(或任何含義)。 如果使用者無論如何都會關閉對話方塊並更改選項卡,則圖示(嚴重或警告,視情況而定)將添加到"聲明"選項卡中。

### <a name="multiple-clicks-to-dismiss-ui"></a>多次按下以關閉 UI

#### <a name="feature-team-goals"></a>功能團隊目標
 不允許使用者在未首先看到說明文本的情況下關閉 UI。

#### <a name="anti-pattern"></a>反模式
 將視訊連結插入 VS UI 中各個位置的團隊根據 UX&times;指定的「關閉按鈕和 工具提示」的常見模式決定,而是實現了下拉和"不再顯示"連結。

#### <a name="example-video-links-in-team-explorer"></a>範例:團隊資源管理員的視訊連結
強制使用者在關閉 UI 之前閱讀解釋性文本是 Visual Studio 中的反模式。 設計正確時,視頻鏈接應顯示一個工具提示,其中包含有關懸停的其他資訊,按&times;下 ""應無需進一步交互即可關閉消息。

 ![解釋性文字反&#45;模式&#45;不正確](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "多次點擊使用不正確")<br />視訊連結模式不正確

使用者被迫使用兩次單擊,只需在視頻鏈接出現的每個位置關閉 UI,而不是簡單的關閉按鈕(一次單擊)。

這種情況的正確設計是遵循 Internet 資源管理器、Office 和 Visual Studio 共有的模式:在懸停時,使用者可以看到工具提示說明,一鍵隱藏 UI。

 ![解譯性文字反&#45;圖案&#45;正確](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "解釋性-模式-正確")<br />正確的視訊連結模式

### <a name="using-command-bars-for-settings"></a>使用命令列設定

**圖 A**表示此反模式:在命令按鈕下方放置一個設置,該設置不僅適用於命令。 在此草圖中,除了"開始調試"之外,還有一些命令(如瀏覽器中的視圖、不調試的啟動和"進入")將尊重所選設置。

![圖 A:命令列反模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "命令巴蘭蒂模式-圖")<br />圖 A:命令列反模式

稍微好一點,但仍然不可取,是把這種類型的設置在工具列中,如圖**B**所示。雖然拆分按鈕佔用的空間較少,因此比下拉清單改進,但兩種設計仍在使用工具列來推廣實際上不是命令的內容。

![圖 B:更好,但仍是命令列反模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "命令巴蘭蒂模式-圖B")<br />圖 B:更好,但仍是命令列反模式

在**圖 C**所示的正確方法中,該設置與一系列命令相關聯。 沒有設置全域設置,我們只是在四個命令之間切換。 這是工具列中命令可接受的唯一情況。

![圖 C:正確使用可視化工作室命令列模式](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "命令巴蘭蒂模式-圖C")<br />圖 C:正確使用可視化工作室命令列模式

### <a name="control-anti-patterns"></a>控制反模式
 某些反模式只是控件或控件元件的使用或表示不正確。

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>底線用作組標籤,而不是超連結
 下劃線文本應僅用於超連結。

 **壞:**\
 ![非超連結的帶下劃線文本是可視化工作室反模式。](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />非超連結的帶下劃線文本是可視化工作室反模式。

 **好:**\
 ![設置正確,非超連結文本在環境字體中顯示為未修飾。](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />設置正確,非超連結文本在環境字體中顯示為未修飾。

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>點選以彈出對話框
 按下「發布 Windows Azure 應用程式」精靈中的「為所有角色啟用遠端桌面」複選框,立即彈出一個對話框,即 Visual Studio 反模式。 此外,選中後,複選框欄位不會填充複選框,這是另一個互動反模式。

 ![單擊複選框後啟動對話框是可視化工作室反模式。](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />單擊複選框後啟動對話框是可視化工作室反模式。

### <a name="hyperlink-anti-patterns"></a>超連結反向模式
 以下範例包含兩個反模式:

1. 懸停時打開紅色的前景表示不使用字體服務中的正確共享顏色。

2. "瞭解更多"不是指向概念主題的連結的適當文本。 用戶的目標不是瞭解更多,它是了解他們選擇的後果。

   ![忽略顏色服務並使用"瞭解更多"的超連結是 Visual Studio 反模式。](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />忽略顏色服務並使用"瞭解更多"的超連結是 Visual Studio 反模式。

**更好的解決方案:** 通過單擊連結提出使用者提出的問題。 例如：

- Windows Azure 服務如何工作?

- 何時需要 Windows Azure 行動服務專案?

#### <a name="using-click-here-for-links"></a>使用「按下此處」查看連結
 超連結應具有自我描述性。 它是一種反模式,使用"點擊這裡"或任何類似的變化。

 **錯誤:**「按一次」的說明。

 **良好:**"如何創建新專案?"
