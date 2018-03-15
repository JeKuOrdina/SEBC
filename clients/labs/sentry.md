To see the sentry roles/rights in Hue Requires: [Assumes ShellBasedUnixGroupsMapping ]

    - The user has to belong to a Sentry Admin group to add/revoke/edit roles and grants on the Server/Database/Table.
        - The group has to be defined on the OS level [All machines or ldap]
        - The group has to be defined in Hue [Manual operation or ldap integration]
        - The user has to be defined on the OS level [All machines or ldap]
        - The user has to be an member of OS group with admin rights. [All machines or ldap]
