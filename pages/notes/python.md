
### python 笔记
https://coderslegacy.com/


``` python
    # 更新 pip
    python -m pip install --upgrade pip

    # python -m pip install --upgrade package_name
    # python -m pip install --user package_name

    pip install pytest
    python3 -m pip install -U pytest --user

    ```
    文件名称 用 test_ 开头
    第一，测试函数必须以 test_ 打头。在测试过程中，pytest 将找出并运行所有以 test_ 打头的函数。
    第二，测试函数的名称应该比典型的函数名更长，更具描述性。
    ```
    
    python -m pytest

```

pip3 show pytest | grep Location

### pygame 
1. 安装 pygame
[pygame](https://www.pygame.org/docs/
```
python3 -m pip install -U pygame --user
python3 -m pygame.examples.aliens
```

图片版权问题 
https://opengameart.org/

**pygame.sprite** 是 Pygame 库中用于精灵（Sprite）管理的核心模块，提供了便捷的类和方法来处理游戏中的角色、道具、敌人等可移动 / 交互元素，简化碰撞检测、动画更新、群体管理等常见游戏开发任务
