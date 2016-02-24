# Emacs' dothash files

Emacs creates dothash files (starting with `.#`) when multiple processes 
are editing the same buffer and there are pending unsaved changes in the buffer.

They are automatically deleted once buffer saved.

You can save all buffers with `M-x save-some-buffers`.
