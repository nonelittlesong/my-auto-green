# [workflow](https://docs.github.com/cn/free-pro-team@latest/actions/reference/workflow-syntax-for-github-actions)

工作流程语法。

## 1. jobs

### 1.1. 常用属性

#### 1.1.1. jobs.<job_id>.outputs

```yml
jobs:
  job1:
    runs-on: ubuntu-latest
    # Map a step output to a job output
    outputs:
      output1: ${{ steps.step1.outputs.test }}
      output2: ${{ steps.step2.outputs.test }}
    steps:
    - id: step1
      # ::set-ouput 设置输出
      run: echo "::set-output name=test::hello"
    - id: step2
      run: echo "::set-output name=test::world"
  job2:
    runs-on: ubuntu-latest
    needs: job1
    steps:
    - run: echo ${{needs.job1.outputs.output1}} ${{needs.job1.outputs.output2}}
```