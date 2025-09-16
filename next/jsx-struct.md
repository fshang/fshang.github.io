## JSX文件结构基础

## 1. 基础组成部分
### 1.1 文件头部声明

```jsx

// React核心库导入（必需）
import React from 'react';
// 其他依赖导入（按需）
import PropTypes from 'prop-types';
import { useState } from 'react';

``` 

### 1.2 组件定义
#### 函数组件（现代推荐）

```jsx

function MyComponent({ prop1, prop2 }) {
  // 组件逻辑区
  const [state, setState] = useState(initialValue);
  
  // 事件处理函数
  const handleClick = () => { /* ... */ };
  
  // JSX渲染区
  return (
    <div className="container">
      {/* 子元素 */}
    </div>
  );
}

```

#### 类组件（传统写法）

```jsx

class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { /* 初始状态 */ };
  }

  componentDidMount() { /* 生命周期方法 */ }

  render() {
    return <div>{this.props.children}</div>;
  }
}

```

## 2. 完整结构要素
### 2.1 类型定义（TypeScript）

``` typescript

interface ComponentProps {
  id: string;
  children?: React.ReactNode;
  onClick: (event: React.MouseEvent) => void;
}

```

### 2.2 样式引入方式

``` jsx

// CSS Modules
import styles from './MyComponent.module.css';
// 内联样式对象
const inlineStyles = { color: 'red' };
// CSS-in-JS
import styled from 'styled-components';

```

### 2.3 上下文使用

``` jsx

const theme = useContext(ThemeContext);

```

## 3. 高级内容
### 3.1 自定义Hook集成

``` jsx

function useCustomHook() {
  /* ... */
}

function Component() {
  const hookValue = useCustomHook();
  /* ... */
}

```

### 3.2 性能优化API

``` jsx

const memoizedComponent = React.memo(MyComponent);
const cachedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

```
### 3.3 副作用处理

``` jsx

useEffect(() => {
  /* 副作用逻辑 */
  return () => {
    /* 清理逻辑 */
  };
}, [dependency]);

useEffect(() => {
  const subscription = props.source.subscribe();
  return () => subscription.unsubscribe(); // 清理函数
}, [props.source]);

```


### 4.完整示例模板

``` jsx

import React, { useState, useEffect } from 'react';
import PropTypes from 'prop-types';
import styles from './Component.module.css';

/**
 * 可复用的展示型组件
 * @param {Object} props - 组件属性
 */
function StandardComponent({ title, items }) {
  const [active, setActive] = useState(false);

  useEffect(() => {
    document.title = title;
  }, [title]);

  const toggleActive = () => setActive(!active);

  return (
    <section className={styles.wrapper}>
      <h2>{title}</h2>
      <ul className={active ? styles.activeList : styles.list}>
        {items.map(item => (
          <li key={item.id}>{item.text}</li>
        ))}
      </ul>
      <button onClick={toggleActive}>
        Toggle
      </button>
    </section>
  );
}

StandardComponent.propTypes = {
  title: PropTypes.string.isRequired,
  items: PropTypes.arrayOf(
    PropTypes.shape({
      id: PropTypes.number,
      text: PropTypes.string
    })
  )
};

export default React.memo(StandardComponent);

```

## 5. 配套文件
### 5.1 样式文件（CSS Modules）

``` css

/* Component.module.css */
.wrapper {
  padding: 1rem;
}
.list {
  display: none;
}
.activeList {
  display: block;
}

```


### 5.2 测试文件（Jest）

``` javascript

import { render, screen } from '@testing-library/react';
import StandardComponent from './StandardComponent';

describe('StandardComponent', () => {
  it('renders title', () => {
    render(<StandardComponent title="Test" items={[]} />);
    expect(screen.getByText('Test')).toBeInTheDocument();
  });
});

```

## 6. 现代React 18+特性
### 6.1 并发模式API

``` jsx

import { startTransition } from 'react';

function Component() {
  const [tab, setTab] = useState('home');
  
  function selectTab(nextTab) {
    startTransition(() => {
      setTab(nextTab);
    });
  }
}

```

### 6.2 服务端组件标记

``` jsx

'use client'; // 客户端组件标记（Next.js 13+）

function ClientComponent() {
  // 使用浏览器API的组件
}

```


### ‌最佳实践建议‌：

1. 使用.jsx扩展名明确区分组件文件
2. 组件文件应保持单一职责原则
3. 复杂组件应拆分为多个子组件
4. 始终为组件添加PropTypes或TypeScript类型定义
5. 样式解决方案应与项目架构保持一致