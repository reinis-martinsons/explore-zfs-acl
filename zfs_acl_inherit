return NULL when ZFS_ACL_DISCARD or creating VLNK
cycle parent acl:
	don't inherit bogus ACEs
	don't inherit ALLOW when ZFS_ACL_NOALLOW
	should ACE be inherited (zfs_ace_can_use):
		if creating VDIR, need ACE_DIRECTORY_INHERIT_ACE or (ACE_FILE_INHERIT_ACE without ACE_NO_PROPAGATE_INHERIT_ACE)
		else need ACE_FILE_INHERIT_ACE
	If owner@, group@, or everyone@ inheritable then zfs_acl_chmod() isn't needed.
	Strip inherited execute permission from file if not in mode
	Strip write_acl and write_owner from permissions when inheriting an ACE
	copy individual ace elements from parent (zfs_set_ace) with ACE_INHERITED_ACE
	Copy special opaque data if any
	If ACE is not to be inherited further, or if the vnode is not a directory, remove all inheritance flags
	For VDIR if only FILE_INHERIT is set then turn on inherit_only
