# GoogleTest


## 基础介绍

C++ 单元测试框架


## 核心内容
```yaml
<gtest/gtest.hpp>:
    testing:
        Bool:
        Combine:
        Environment:
        Range:
        Test: # 测试基类
            SetUp():
            TearDown():
        TestWithParam:
        Types:
        Values:
        ValuesIn:
        WithParamInterface:
        AddGlobalTestEnvironment():
        InitGoogleTest():
    ADD_FAILURE():
    ASSERT_EQ():
    EXPECT_EQ():
    INSTANTIATE_TEST_SUITE_P():
    REGISTER_TYPED_TEST_SUITE_P():
    RUN_ALL_TESTS(): # 运行所有测试用例
    SUCCESS():
    TEST(): # 测试用例
    TEST_F():
    TEST_P(): # 参数化测试
    TYPED_TEST():
    TYPED_TEST_SUITE():
```


