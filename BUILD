python_requirements(name="reqs")


def django_util(name, **kwargs):
    pex_binary(
        name=name,
        dependencies=[
            ":reqs#django",
        ],
        **kwargs
    )


django_util("django", entry_point="django")
django_util("django-admin", script="django-admin")
