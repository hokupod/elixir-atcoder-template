# Elixir AtCoder Template

This is a template for competitive programming in Elixir using devbox and online-judge-tools.
This template is primarily intended for using Elixir for competitive programming on AtCoder.

## Setup

1.  Ensure you have [devbox](https://www.jetify.com/devbox/docs/installing-devbox/) installed.
2.  Run `devbox shell` to activate the development environment.
3.  Inside the devbox shell, run `devbox run configure-acc` to set up the `acc` (AtCoder CLI) tool with the Elixir template.

## Usage

1.  To create a new problem workspace (e.g., for `abc100_a`):

## Logging into AtCoder (Important)

To submit your solutions or download test cases for some contests, you need to log in to AtCoder using `oj`.

1.  Run the login command:
    ```bash
    oj login https://atcoder.jp/
    ```
2.  You will be prompted for your username and password.

**Known Issue with Cloudflare CAPTCHA:**

Currently, AtCoder's use of Cloudflare CAPTCHA may prevent `oj login` from working directly. If you encounter issues, you may need to manually set the session cookie:

1.  Log in to AtCoder in your web browser.
2.  Open your browser's developer tools (usually by pressing F12).
3.  Go to the "Application" (or "Storage") tab and find the cookies for `atcoder.jp`.
4.  Copy the value of the `REVEL_SESSION` cookie.
5.  Find the `cookie.jar` file used by `oj`. The path is usually displayed when `oj login` fails (e.g., `/home/${USER}/.local/share/online-judge-tools/cookie.jar` or similar depending on your OS).
6.  Open `cookie.jar` in a text editor and replace the line for `REVEL_SESSION` with the value you copied. It should look something like:
    ```
    #LWP-Cookies-2.0
    Set-Cookie3: REVEL_FLASH=""; path="/"; domain="atcoder.jp"; path_spec; secure; discard; HttpOnly=None; version=0
    Set-Cookie3: REVEL_SESSION="<your_copied_value>"; path="/"; domain="atcoder.jp"; path_spec; secure; expires="<timestamp>"; HttpOnly=None; version=0
    ```
    You need to replace `"<your_copied_value>"` with the actual value you copied from your browser. The `expires` timestamp will likely be different. The important part is to update the `REVEL_SESSION` value.

For more details on this issue, see: [online-judge-tools/oj#934](https://github.com/online-judge-tools/oj/issues/934)

## Creating a New Problem

1.  To create a new problem workspace (e.g., for `abc100_a`):
    ```bash
    npx acc new abc100_a
    ```
    This will create a new directory (e.g., `abc100_a`) with `main.exs` and test cases.
2.  Navigate to the problem directory:
    ```bash
    cd abc100_a
    ```
3.  Implement your solution in `main.exs`.
4.  To test your solution:
    ```bash
    oj test -c "elixir main.exs"
    ```

## Submitting Your Solution

Once you are confident in your solution, you can submit it using `oj`.

1.  Ensure you are in the problem directory (e.g., `abc100_a`).
2.  Submit your solution file (e.g., `main.exs`):
    ```bash
    oj submit main.exs
    ```
    Alternatively, you can often submit using the problem URL:
    ```bash
    oj submit <problem_url>
    ```
    The command might vary slightly based on the contest system and your setup.

For detailed usage and options for the submit command, please refer to the official `online-judge-tools` documentation or use the help command:
```bash
oj submit --help
```

## Files

*   `devbox.json`: Defines the development environment using devbox.
*   `devbox.lock`: Locks the package versions for reproducible environments.
*   `.gitignore`: Specifies intentionally untracked files that Git should ignore.
*   `template/`: Contains the template files for `acc new`.
    *   `template/template.json`: Configuration for `acc`.
    *   `template/main.exs`: The Elixir template file.
