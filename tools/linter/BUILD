package(
    default_python_interpreter = 'python3',
    python_module_dir = '',
)

filegroup(
    name = 'rule_args',
    srcs = ['//src/parse/args'],
)

python_binary(
    name = 'linter',
    out = 'linter',
    main = 'linter.py',
    resources = [':rule_args'],
    visibility = ['PUBLIC'],
)

python_test(
    name = 'linter_test',
    srcs = ['linter_test.py'],
    data = ['test_data'],
    deps = [
        ':linter',
    ],
)

genrule(
    name = 'help_topics',
    srcs = {
        'linter': ['linter.py'],
        'script': ['linter_help.py'],
    },
    outs = ['help.json'],
    cmd = 'cat $SRCS_LINTER | python $SRCS_SCRIPT > $OUT',
    visibility = ['//src/help/...'],
)
