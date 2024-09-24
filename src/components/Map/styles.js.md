## Material-UI Styles for Map Component

**Table of Contents**

* [1. Introduction](#1-introduction)
* [2. Usage](#2-usage)
* [3. Styles](#3-styles)
    * [3.1 `paper`](#31-paper)
    * [3.2 `mapContainer`](#32-mapcontainer)
    * [3.3 `markerContainer`](#33-markercontainer)
    * [3.4 `pointer`](#34-pointer)

### 1. Introduction

This code defines Material-UI styles for a map component using the `makeStyles` function. 

### 2. Usage

This code is intended to be used in a React component that renders a map. The styles can be applied to elements within the component using the `classes` object returned by the `makeStyles` function.

### 3. Styles

#### 3.1 `paper`

| Property | Value | Description |
|---|---|---|
| `padding` | `'10px'` | Sets padding for the element. |
| `display` | `'flex'` | Enables flexbox layout. |
| `flexDirection` | `'column'` | Arranges items vertically. |
| `justifyContent` | `'center'` | Centers items vertically. |
| `width` | `'100px'` | Sets the width of the element. |

#### 3.2 `mapContainer`

| Property | Value | Description |
|---|---|---|
| `height` | `'85vh'` | Sets the height of the container to 85% of the viewport height. |
| `width` | `'100%'` | Sets the width of the container to 100%. |

#### 3.3 `markerContainer`

| Property | Value | Description |
|---|---|---|
| `position` | `'absolute'` | Positions the element relative to its parent. |
| `transform` | `'translate(-50%, -50%)'` | Centers the element using the `transform` property. |
| `zIndex` | `1` | Sets the z-index of the element to 1. |
| `&:hover` | `zIndex: 2` | Increases the z-index to 2 on hover, making the element appear on top. |

#### 3.4 `pointer`

| Property | Value | Description |
|---|---|---|
| `cursor` | `'pointer'` | Sets the cursor to a pointer on hover. | 
