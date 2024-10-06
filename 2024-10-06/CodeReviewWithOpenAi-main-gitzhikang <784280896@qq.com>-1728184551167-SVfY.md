The provided Git diff records show changes to a GitHub Actions workflow and several Java classes within a project named `openai-code-review-sdk`. Here's a summary of the changes:

### GitHub Actions Workflow Change (`main-maven-jar.yml`):

- A new secret variable `PROMPT` is added to the workflow's environment variables. This suggests that the workflow might use this variable for some form of prompting or customization.

### Java Classes Changes:

#### `OpenAiCodeReview.java`:
- The constructor for `OpenAiCodeReview` now takes an additional parameter for the `PROMPT` environment variable, which is retrieved using `getEnv("PROMPT")`. This indicates that the `ChatGLM` class, which is likely a concrete implementation of `IOpenAI`, is being passed a `PROMPT` value.

#### `AbstractOpenAiCodeReviewService.java`:
- The `codeReview` method now takes an additional parameter for the `prompt`. This method is now an abstract method in the `AbstractOpenAiCodeReviewService` class, which means all subclasses must implement this method with the new parameter.

#### `OpenAiCodeReviewService.java`:
- The `codeReview` method in `OpenAiCodeReviewService` now takes the `prompt` as a parameter. This method constructs a `ChatCompletionRequestDTO` with the `prompt` and the `diffCode` before sending it to the `IOpenAI` implementation.

#### `IOpenAI.java`:
- An additional method `getPrompt()` is added to the `IOpenAI` interface. This suggests that the implementation classes of `IOpenAI` should be able to provide a `prompt`.

#### `ChatGLM.java`:
- The constructor for `ChatGLM` is updated to take a `prompt` parameter, and the `getPrompt()` method is implemented to return the `prompt` value passed during construction.

### Conclusion:
These changes appear to be related to enhancing the functionality of the `openai-code-review-sdk` by integrating a `PROMPT` into the code review process. The `PROMPT` is likely used to customize the initial message sent to the AI for code review purposes, which could affect the AI's response and the quality of the code review. The introduction of this prompt as a secret variable and its integration into the code review workflow and service methods indicates a new or enhanced feature for the code review tool.