# sql_test
1.Для	заданного	списка	товаров	получить	названия	всех	категории ,	в	которых	
    представлены	товары.	
    
    
        SELECT title FROM categories WHERE id IN (SELECT category_id FROM products WHERE id IN (1,5,6,7,19)) ORDER by title ASC;;
        
        
2.Для	заданнои категории	получить	список	предложении всех	товаров	из	этои 
  категории.	Каждая	категория	может	иметь	несколько	подкатегории .	  
  
  
        SELECT p.title FROM categories AS c LEFT JOIN categories AS ch ON ch.parent_id = c.id LEFT JOIN products AS p ON p.category_id = c.id OR p.category_id = ch.id WHERE c.id = 1 GROUP BY p.id ORDER by
         p.title ASC;
        
        
        
3.Для	заданного	списка	категории получить	количество	уникальных	товаров	в	
каждои категории.	


        SELECT COUNT(DISTINCT(p.id)) AS count FROM categories AS c LEFT JOIN categories AS ch ON ch.parent_id = c.id LEFT JOIN products AS p ON p.category_id = c.id OR p.category_id = ch.id WHERE c.id IN (1,5,12,13) ORDER by p.title ASC;
        
4.Для	заданного	списка	категории получить	количество	единиц	каждого	товара	
которыи входит	в	указанные	категории.	
        
        
        SELECT p.amount AS count FROM categories AS c LEFT JOIN categories AS ch ON ch.parent_id = c.id LEFT JOIN products AS p ON p.category_id = c.id OR p.category_id = ch.id WHERE c.id IN (1,5,12,13) G
        ROUP BY p.id ORDER by p.title ASC;