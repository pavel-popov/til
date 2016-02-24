# Getting CLOB value from XMLType in PL/SQL

There is `.getClobVal()` method of XMLType, thus you can get CLOB value.

Example:

    CREATE TABLE item (id NUMBER, name VARCHAR2(30));
    
    INSERT INTO item (id, name)
    SELECT 1, 'asdf' FROM dual UNION ALL
    SELECT 2, 'qwer' FROM dual;
  
    CREATE OR REPLACE PROCEDURE sp_xml (id_in IN NUMBER, xml_out OUT CLOB)
    IS
    BEGIN
      SELECT XMLElement("item",
                XMLForest(
                  id as "id",
                  name as "name")).getClobVal()
        INTO xml_out
        FROM item
       WHERE id = id_in;
    END;
    /
