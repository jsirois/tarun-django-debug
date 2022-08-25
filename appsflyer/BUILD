python_sources()

resource(
    name="env",
    source=".env"
)

pex_binary(
    name="manage",
    entry_point="manage.py",
    dependencies=[
        "./appsflyer:appsflyer",
        ":env"
    ],
    restartable=True
)

