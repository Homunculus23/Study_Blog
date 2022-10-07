# 自我介绍
我学习过的编程相关技能有 `HTML` `CSS` `JS``TS`等等，以下是我写过的部分代码：
```JS
export const Tabs = defineComponent({
  props: {
    selected: {
      type: String as PropType<string>,
      required: false,
    }
  },
  setup: (props, context) => {
    return () => {
        const tabs = context.slots.default?.()
        if (!tabs) return () => null
        for (let i = 0; i < tabs.length; i++) {
            if (tabs[i].type !== Tab) {
            throw new Error('<Tabs> only accepts <Tab> as children')
            }
        }
        return <div class={s.tabs}>
            <ol class={s.tabs_nav}>
                {
                    tabs.map(item =>
                        <li class={item.props?.name === props.selected ? s.selected : ''}
                            onClick={() => context.emit('update:selected', item.props?.name)}>
                            {item.props?.name}
                        </li>
                    )
                }
            </ol>
            <div>
                {tabs.find(item => item.props?.name === props.selected)}
            </div>
        </div>
    }
  }
})
```
目前正在加深学习前端相关的技能。
