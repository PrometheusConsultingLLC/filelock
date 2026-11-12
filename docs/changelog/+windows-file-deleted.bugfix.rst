:class:`~filelock.FileLock` on Windows no longer raises :class:`PermissionError` when opening the lock file races a
peer's completed unlink of it. ``NtCreateFile`` answers that open ``STATUS_FILE_DELETED``, which is now retried
within the timeout like a delete-pending name. A genuine access denial still raises.
