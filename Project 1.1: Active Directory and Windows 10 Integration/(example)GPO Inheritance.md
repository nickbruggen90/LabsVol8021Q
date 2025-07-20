### GPO Scope by OU Level

- **testlab.local** (Domain root)
  - **Scope:** GLOBAL - affects entire domain
  - **Company**
    - **Scope:** All company objects
    - **Users**
      - **Scope:** All company users
      - **Sales** → Sales department only
      - **IT** → IT department only  
      - **HR** → HR department only
    - **Computers**
      - **Scope:** All company computers
      - **Workstations** → User computers only
      - **Servers** → Server computers only
    - **Groups** → Group objects only
  - **Built-in containers** → System accounts, default groups

Both formats work great in markdown! The first uses code blocks to preserve the tree structure, the second uses nested lists. 📝
