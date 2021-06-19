---
title: 將追蹤屬性新增至 DSL 定義
description: 深入瞭解追蹤定義域屬性，以及如何將追蹤屬性新增至網域模型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384911"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>在特定領域語言定義中新增追蹤屬性

本逐步解說將示範如何將追蹤屬性新增至網域模型。

*追蹤定義域* 屬性是使用者可以更新的屬性，但是它的預設值是使用其他定義域屬性或專案的值來計算。

例如，在 [Domain-Specific 語言工具] (DSL 工具]) 中，網域類別的 [顯示名稱] 屬性的預設值是使用網域類別的名稱計算，但是使用者可以在設計階段變更值，或將它重設為計算值。

在這個逐步解說中，您將建立特定領域語言 (DSL) 具有命名空間追蹤屬性，此屬性的預設值是以模型的預設 Namespace 屬性為基礎。 如需追蹤屬性的詳細資訊，請參閱 [定義追蹤屬性](/previous-versions/cc825929(v=vs.100))。

- DSL 工具支援追蹤屬性描述項。 但是，DSL 設計工具無法用來將追蹤屬性新增至語言。 因此，您必須加入自訂程式碼來定義和執行追蹤屬性。

  追蹤屬性有兩個狀態： [追蹤] 和 [由使用者更新]。 追蹤屬性有下列功能：

- 當處於追蹤狀態時，會計算追蹤屬性的值，而且此值會隨著模型中的其他屬性變更而更新。

- 當在使用者狀態更新時，追蹤屬性的值會保留使用者上次設定屬性的值。

- 在 [ **屬性** ] 視窗中，[追蹤] 屬性的 [ **重設** ] 命令只會在屬性位於 [依使用者狀態更新] 時啟用。 **Reset** 命令會將追蹤屬性狀態設定為 [追蹤]。

- 在 [ **屬性** ] 視窗中，當追蹤屬性處於追蹤狀態時，它的值會以一般字型顯示。

- 在 [ **屬性** ] 視窗中，當追蹤屬性處於 [依使用者狀態更新] 時，其值會以粗體字顯示。

## <a name="prerequisites"></a>必要條件

開始這個逐步解說之前，您必須先安裝這些元件：

| 元件 | 連結 |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>建立專案

1. 建立 Domain-Specific 語言設計工具專案。 請命名為 `TrackingPropertyDSL`。

2. 在 **特定領域語言設計工具 Wizard** 中，設定下列選項：

    1. 選取 [ **MinimalLanguage** ] 範本。

    2. 使用網域特定語言的預設名稱 `TrackingPropertyDSL` 。

    3. 將模型檔案的副檔名設定為 `trackingPropertyDsl` 。

    4. 使用模型檔案的預設範本圖示。

    5. 將產品的名稱設定為 `Product Name` 。

    6. 將公司名稱設定為 `Company Name` 。

    7. 針對方案中的專案，使用根命名空間的預設值 `CompanyName.ProductName.TrackingPropertyDSL` 。

    8. 允許嚮導為您的元件建立強式名稱金鑰檔。

    9. 檢查解決方案的詳細資料，然後按一下 **[完成]** 以建立 DSL 定義專案。

## <a name="customize-the-default-dsl-definition"></a>自訂預設 DSL 定義
 在本節中，您會自訂 DSL 定義以包含下列專案：

- 模型中每個元素的命名空間追蹤屬性。

- 模型中每個元素的布林 IsNamespaceTracking 屬性。 這個屬性會指出追蹤屬性是處於追蹤狀態，還是在依使用者狀態更新。

- 模型的預設命名空間屬性。 這個屬性將用來計算命名空間追蹤屬性的預設值。

- 模型的 CustomElements 計算屬性。 這個屬性會指出具有自訂命名空間的元素比例。

### <a name="to-add-the-domain-properties"></a>若要加入定義域屬性

1. 在 [DSL 設計工具] 中，以滑鼠右鍵按一下 [ **examplemodel.store.customer** ] 網域類別，指向 [ **加入**]，然後按一下 [ **DomainProperty**]。

    1. 命名新的屬性 `DefaultNamespace` 。

    2. 在新屬性的 [ **屬性** ] 視窗中，將 [ **預設值** ] 設定為 `DefaultNamespace` ，並將 [ **類型** ] 設定為 [ **字串**]。

2. 針對 **examplemodel.store.customer** 網域類別，新增名為的網域屬性 `CustomElements` 。

     在新屬性的 [ **屬性** ] 視窗中，將 [ **類型** ] 設定為 [ **計算**]。

3. 針對 **ExampleElement** 網域類別，新增名為的網域屬性 `Namespace` 。

     在新屬性的 [ **屬性** ] 視窗中，將 [可 **流覽** ] 設定為 [ **False**]，並將 **種類** 設定為 [ **CustomStorage**]。

4. 針對 **ExampleElement** 網域類別，新增名為的網域屬性 `IsNamespaceTracking` 。

     在新屬性的 [ **屬性** ] 視窗中，將 [可 **流覽** ] 設為 **False**、將 [ **預設值** ] 設定為 `true` ，並將 [ **類型** ] 設定為 [ **布林** 值

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>更新圖表元素和 DSL 詳細資料

1. 在 DSL 設計工具中，以滑鼠右鍵按一下 [ **ExampleShape** 幾何] 圖形，指向 [ **加入**]，然後按一下 [ **文字** 裝飾專案]。

    1. 為新的文字裝飾專案命名 `NamespaceDecorator` 。

    2. 在文字裝飾專案的 [ **屬性** ] 視窗中，將 [ **位置** ] 設定為 [ **InnerBottomLeft**]。

2. 在 [DSL 設計工具] 中，選取將 **ExampleElement** 類別連接到 [ **ExampleShape** ] 圖形的程式程式碼。

    1. 在 [ **DSL 詳細資料** ] 視窗中，選取 [裝飾專案 **對應** ] 索引標籤。

    2. 在 [ **裝飾專案** ] 清單中，選取 [ **NamespaceDecorator**]，選取其核取方塊，然後在 [ **顯示內容** ] 清單中選取 [ **命名空間**]。

3. 在 [ **DSL Explorer**] 中，展開 [ **網域類別** ] 資料夾，在 [ **ExampleElement** ] 節點上按一下滑鼠右鍵，然後按一下 [ **加入新的定義欄位型別描述** 元]。

    1. 展開 [ **ExampleElement** ] 節點，然後選取 **自訂類型描述元 (網欄位型別描述元)** 節點。

    2. 在定義欄位型別描述項的 [ **屬性** ] 視窗中，將 [ **自訂編碼** ] 設定為 [ **True**]。

4. 在 [ **DSL Explorer**] 中，選取 [ **Xml 序列化行為** ] 節點。

    1. 在 [ **屬性** ] 視窗中，將 **自訂的 Post 載入** 設定為 **True**。

## <a name="transform-templates"></a>轉換範本

現在您已定義 DSL 的網域類別和屬性，您可以確認 DSL 定義可以正確轉換，以重新產生專案的程式碼。

1. 在 [ **方案總管** ] 工具列上，按一下 [ **轉換所有範本**]。

2. 系統會重新產生解決方案的程式碼，並儲存 Dsldefinition.dsl 檔。 如需有關定義檔之 XML 格式的詳細資訊，請參閱[dsldefinition.dsl 檔。](../modeling/the-dsldefinition-dsl-file.md)

## <a name="create-files-for-custom-code"></a>建立自訂程式碼的檔案

當您轉換所有範本時，系統會產生原始程式碼，在 Dsl 和 DslPackage 專案中定義您的特定領域語言。 如此一來，您就可以避免干擾產生的文字，而是將自訂程式碼寫在與產生的程式碼檔案不同的檔案中。

您必須提供程式碼來維護追蹤屬性的值和狀態。 為了協助您區別自訂程式碼與產生的程式碼，並避免檔案命名衝突，請將自訂程式碼檔案放在不同的子資料夾中。

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **DSL** 專案，指向 [ **加入**]，然後按一下 [ **新增資料夾**]。 將新資料夾命名為 `CustomCode` 。

2. 以滑鼠右鍵按一下新的 [ **CustomCode** ] 資料夾，指向 [ **加入**]，然後按一下 [ **新增專案**]。

3. 選取程式 **代碼** 檔案範本，將 **名稱** 設定為 `NamespaceTrackingProperty.cs` ，然後按一下 **[確定]**。

     會建立並開啟 NamespaceTrackingProperty .cs 檔案進行編輯。

4. 在資料夾中，建立下列程式碼檔案： `ExampleModel.cs,``HelperClasses.cs` 、 `Serialization.cs` 和 `TypeDescriptor.cs` 。

5. 在 **DslPackage** 專案中，也建立 `CustomCode` 資料夾，並將它新增至程式 `Package.cs` 代碼檔案。

## <a name="add-helper-classes-to-support-tracking-properties"></a>新增 Helper 類別以支援追蹤屬性

在 HelperClasses .cs 檔案中，加入和類別，如下所 `TrackingHelper` `CriticalException` 示。 您稍後將在本逐步解說中參考這些類別。

1. 將下列程式碼新增至 HelperClasses .cs 檔案。

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>新增自訂類型描述元的自訂程式碼

`GetCustomProperties`針對網域類別的型別描述元執行方法 `ExampleModel` 。

> [!NOTE]
> DSL 工具為呼叫的自訂類型描述元所產生的程式碼 `ExampleModel` `GetCustomProperties` ; 不過，dsl 工具不會產生可執行方法的程式碼。

定義此方法會建立命名空間追蹤屬性的追蹤屬性描述元。 此外，提供追蹤屬性的屬性可讓 [ **屬性** ] 視窗正確地顯示內容。

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>若要修改 Examplemodel.store.customer 網域類別的類型描述元

1. 將下列程式碼加入至 .cs 檔案。

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>新增封裝的自訂程式碼

產生的程式碼會定義 ExampleElement 網域類別的型別描述提供者。不過，您必須加入程式碼，指示 DSL 使用此類型描述提供者。

1. 將下列程式碼加入至封裝 .cs 檔案。

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>新增模型的自訂程式碼

執行 `GetCustomElementsValue` 網域類別的方法 `ExampleModel` 。

> [!NOTE]
> DSL 工具為呼叫產生的程式碼 `ExampleModel` `GetCustomElementsValue` ; 不過，dsl 工具不會產生可執行方法的程式碼。

定義 `GetCustomElementsValue` 方法會提供的 CustomElements 計算屬性邏輯 `ExampleModel` 。 這個方法 `ExampleElement` 會計算具有命名空間追蹤屬性（具有使用者更新值）之網域類別的數目，並傳回代表此計數的字串，做為模型中總元素的比例。

此外，將方法新增 `OnDefaultNamespaceChanged` 至 `ExampleModel` ，並覆寫的 `OnValueChanged` `DefaultNamespacePropertyHandler` 嵌套類別的方法 `ExampleModel` 以呼叫 `OnDefaultNamespaceChanged` 。

因為 DefaultNamespace 屬性是用來計算命名空間追蹤屬性，所以 `ExampleModel` 必須通知所有 `ExampleElement` 網域類別 DefaultNamespace 的值已變更。

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>若要修改追蹤屬性的屬性處理常式

1. 將下列程式碼新增至 Examplemodel.store.customer .cs 檔案。

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>新增追蹤屬性的自訂程式碼

將 `CalculateNamespace` 方法加入至 `ExampleElement` 網域類別。

定義此方法會提供的 CustomElements 計算屬性邏輯 `ExampleModel` 。 這個方法 `ExampleElement` 會計算具有命名空間追蹤屬性的網域類別數目，而此屬性是由使用者狀態更新，並傳回代表此計數的字串，做為模型中總元素的比例。

此外，新增、和方法的儲存區，以取得和設定網域類別的命名空間自訂儲存體屬性 `ExampleElement` 。

> [!NOTE]
> DSL 工具為了 `ExampleModel` 呼叫 get 和 set 方法所產生的程式碼; 不過，Dsl 工具不會產生可執行方法的程式碼。

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>若要加入自訂類型描述元的方法

1. 將下列程式碼新增至 NamespaceTrackingProperty .cs 檔案。

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>新增自訂程式碼以支援序列化

加入程式碼以支援 XML 序列化的自訂後續載入行為。

> [!NOTE]
> DSL 工具產生的程式碼會呼叫 `OnPostLoadModel` 和 `OnPostLoadModelAndDiagram` 方法，不過，dsl 工具不會產生可執行這些方法的程式碼。

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>加入程式碼以支援自訂的後續載入行為

1. 將下列程式碼加入至序列化 .cs 檔案。

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>測試語言

下一步是在新的實例中建立及執行 DSL 設計工具， [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 讓您可以確認追蹤屬性是否正常運作。

1. 在 [建置] 功能表上，按一下 [重建方案]。

2. 在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。

    的實驗性組建 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 會開啟包含空白測試檔案的 **調試** 程式。

3. 在 **方案總管** 中，按兩下 trackingPropertyDsl 檔案，在設計工具中開啟它，然後按一下設計介面。

    請注意，在圖表的 [ **屬性** ] 視窗中，[ **預設命名空間** ] 屬性是 [ **DefaultNamespace**]，而 [ **自訂元素** ] 屬性是 **0/0**。

4. 將 **ExampleElement** 元素從 [ **工具箱** ] 拖曳至圖表介面。

5. 在專案的 [ **屬性** ] 視窗中，選取 [ **element Namespace** ] 屬性，然後將值從 **DefaultNamespace** 變更為 **OtherNamespace**。

    請注意， **元素命名空間** 的值現在以粗體顯示。

6. 在 [ **屬性** ] 視窗中，以滑鼠右鍵按一下 [ **元素命名空間**]，然後按一下 [ **重設**]。

    屬性的值會變更為 **DefaultNamespace**，而此值會以一般字型顯示。

    再以滑鼠右鍵按一下 **元素命名空間** 。 **重設** 命令現在已停用，因為屬性目前處於其追蹤狀態。

7. 將另一個 **ExampleElement** 從 [ **工具箱** ] 拖曳至圖表介面，然後將它的 **元素命名空間** 變更為 **OtherNamespace**。

8. 按一下設計介面。

    在圖表的 [ **屬性** ] 視窗中， **自訂元素** 的值現在是 **1/2**。

9. 將圖表的 **預設命名空間** 從 **DefaultNamespace** 變更為 **NewNamespace**。

     第一個元素的 **命名空間** 會追蹤 **預設命名空間** 屬性，而第二個元素的 **命名空間** 會保留其使用者更新的 **OtherNamespace** 值。

10. 儲存方案，然後關閉實驗組建。

## <a name="next-steps"></a>後續步驟

如果您打算使用一個以上的追蹤屬性，或在多個 DSL 中執行追蹤屬性，您可以建立文字模板來產生支援每個追蹤屬性的通用程式碼。 如需文字模板的詳細資訊，請參閱程式 [代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)